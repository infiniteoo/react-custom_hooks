# Creating Custom React Hooks (A Fun Example)

## Live Demo:
http://funnygifs.netlify.app

![example_gif](./example.gif)



## About

A very simple project utilizing the GIPHY random gif generator API to showcase a basic, everyday use of how to create custom hooks within React.

The two main components used in this app that are displayed in the UI are "Random" and "Tag".  The Random component simply pulls a random gif from the GIPHY database, while the Tag component lets the user type in a keyword to search and display.  

Naturally, these two components would share the exact same codebase, with the exception of adding an extra string to the API query with the keyword. Rather than have two components executing basically the same code, you can create a custom hook that does the work for both of the components, but allows customization by sending a search team to the API in the form of our "tag".

the useGIf hook is what we use:

```
const useGif = (tag) => {
  const [gif, setGif] = useState("");

  const fetchGif = async (tag) => {
    const { data } = await axios.get(tag ? `${url}&tag=${tag}` : url);

    const imageSrc = data.data.images.downsized_large.url;
    setGif(imageSrc);
  };

  useEffect(() => {
    fetchGif(tag);
  }, [tag]);

  return { gif, fetchGif };
};
```


Built With:

* React
* Hooks
* GIPHY
* axios
* .env
* Netlify
