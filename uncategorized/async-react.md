#async data in a React component

## Using `Promise`
```
class Foo extends Component {
  constructor(props) {
    super(props);

    this.state = {
      loading: true;
    }
  }

  componentDidMount() {
    const data =  fetch().then((data) => {
        this.setState({
            loading: false,
            data
        });
      });
  }

  render () {
    const {data, loading } = this.state;

    return ({loading ? < loading /> : <view ...data /> });
  }
}
```


## Using `async await`
```
class Foo extends Component {
  constructor(props) {
    super(props);

    this.state = {
      loading: true;
    }
  }

  async componentDidMount() {
    const data = await fetchData();

    this.setState({
        loading: false,
        data
    });
  }

  render () {
    const {data, loading } = this.state;

    return ({loading ? < loading /> : <view ...data /> });
  }
}
```
