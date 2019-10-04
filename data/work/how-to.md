# adding to show your work

We'd love you to work in public this year, sharing your ideas even in their development stages (like you'll find [this guy]([https://www.amazon.com/Show-Your-Work-Austin-Kleon/dp/076117897X/ref=sr_1_1?keywords=show+your+work&qid=1570210084&sr=8-1](https://www.amazon.com/Show-Your-Work-Austin-Kleon/dp/076117897X/ref=sr_1_1?keywords=show+your+work&qid=1570210084&sr=8-1)) suggesting). To accomplish this, we've created a little route on [show.learninglab.xyz](https://show.learninglab.xyz) that will serve up markdown files that are stored in the [gitub repo](https://github.com/mkuzmick/the-show/tree/master/data/work).

```
router.get('/:id', async function (req, res, next) {
  var markdownFiles = fs.readdirSync(path.join(ROOT_DIR, 'data/work'));
  if (markdownFiles.includes(`${req.params.id}.md`)) {
    fs.readFile(path.join(ROOT_DIR, 'data/work', `${req.params.id}.md`), {encoding: 'utf-8'}, (err, data) => {
      if (err) {res.send("check back in a minute")};
      console.log(data);
      res.render("work",  {
        title: `markdown for ${req.params.id}`,
        convertedMarkdown: marked(data)
      });
    });
  } else {
    res.render('test', {title: "nothing here just yet.", data: JSON.stringify(markdownFiles, null, 4)});
  }
});
```

1. open [stackedit.io]([https://stackedit.io/app#](https://stackedit.io/app#)) on your machine.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwMzY2MDQyNl19
-->