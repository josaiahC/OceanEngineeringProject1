class Markdown extends React.Component {
    constructor(props) {
      super(props);
      
      // replace with your URL, obviously
      this.baseUrl = 'https://raw.githubusercontent.com/davidgilbertson/about-github/master/text-snippets';
      
      this.state = {
        markdown: '',
      };
    }

    componentDidMount() {
      fetch(`${this.baseUrl}/${this.props.url}`)
        .then(response => response.text())
        .then((markdown) => {
          this.setState({markdown});
        });
    }

    render() {
      return (
        <div dangerouslySetInnerHTML={{__html: marked(this.state.markdown)}} />
      );
    }
}
