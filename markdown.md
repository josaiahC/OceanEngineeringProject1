class Markdown extends React.Component {
    constructor(props) {
      super(props);
      
      // replace with your URL, obviously
      this.baseUrl = 'https://github.com/josaiahC/OceanEngineeringProject1/blob/master/README.md';
      
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
