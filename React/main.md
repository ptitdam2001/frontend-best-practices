# React best practices



### It's just a view library

Let's get the basics out of the way. React is not another MVC framework, or any other kind of framework. It's just a library for rendering your views. If you're coming from the MVC world, you need to realize that React is just the 'V', part of the equation, and you need to look elsewhere when it comes to defining your 'M' and 'C', otherwise you're going to end up with some really yucky React code. More on that later.

### Keep your components small

This might seem like an obvious one, but it's worth calling out. Every good developer knows that small classes/modules/whatever are easier to understand, test, and maintain, and the same is true of React components. Of course, the exact size will depend upon many different factors (including you and your team's personal preference!), but in general you should make your components significantly smaller than you think they need to be. 

As an example, here is the component that shows a list of blog entries:

```js
const LatestPostsComponent = props => (
  <section>
    <div><h1>Latest posts</h1></div>
    <div>
      { props.posts.map(post => <PostPreview key={post.slug} post={post}/>) }
    </div>
  </section>
);
```

The component itself is a `<section>`, with only 2 `<div>`s inside it. The first one has a heading, and second one just maps over some data, rendering a `<PostPreview>` for each element. That last part, extracting the `<PostPreview>` as its own component, is the important bit. I think this is a good size for a component.



=> https://github.com/markerikson/react-redux-links/blob/master/react-architecture.md