# Use Jest to test axios with nock http mocks
```js
//create-fetch.js
import axios from 'axios';
import HttpStatus from 'http-status-codes';
// NavigationService is an implementation
// of https://reactnavigation.org/docs/en/navigating-without-navigation-prop.html
import NavigationService from '@services/navigation-service';

async function createFetch({
  data = null,
  headers = {},
  method = 'get',
  params = {},
  accessToken = null,
  url = '',
  withCredentials = false,
}) {
  const requestHeaders = {
    ...(accessToken !== null && { authorization: `Bearer ${accessToken}` }),
    ...headers,
  };

  const instance = axios.create({ headers: requestHeaders });

  instance.interceptors.response.use(response => response, error => {
    if(error && error.response?.status === HttpStatus.FORBIDDEN) {
      NavigationService.navigate('Login');
      return false;
    }
    return error;
  });

  return instance.request({
    method,
    params,
    url,
    withCredentials,
    data: data ? JSON.stringify(data) : null,
  });
}

export default createFetch;
```


```js
// create-fetch.spec.js
import axios from 'axios';
import httpAdapter from 'axios/lib/adapters/http';
import nock from 'nock';
import HttpStatus from 'http-status-codes';
import createFetch from '../create-fetch';

describe('createFetch', () => {
  const host = 'http://testhost';
  axios.defaults.host = host;
  axios.defaults.baseURL = host;  // <-- important bit to make axios and nock work togethers
  axios.defaults.adapter = httpAdapter;


  const mockRef = {
  	dispatch: jest.fn(),
  };
  mockNavigationService.setTopLevelNavigator(mockRef);

  it('intercepts 403', async () => {
  	const url = '/test';

  	nock(host).get(url).reply(HttpStatus.FORBIDDEN);

  	const response = await createFetch({ url });

  	expect(mockRef.dispatch).toHaveBeenCalledWith({ routeName: 'Login', type: 'Navigation/NAVIGATE' });
  	expect(response).toEqual(false);
  });

  it('returns a valid response', async () => {
  const url = '/test/test';
  const mockResponse = { key: 'value' };

  nock(host).get(url).reply(HttpStatus.OK, JSON.stringify(mockResponse));

  const response = await createFetch({ url });
  expect(response.data).toEqual(mockResponse);
  });
});
```
