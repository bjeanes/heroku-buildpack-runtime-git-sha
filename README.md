# heroku-buildpack-runtime-git-sha

Record the pushed Git SHA in the slug so it can be inspected at dyno runtime.

**IT DOES NOT WORK**: Heroku pushes happen in a pre-receive hook, which means the SHA being pushed hasn't actually been committed
to the server-side repo yet. The best this buildpack does is exposes the *previous* SHA. The buildpack scripts don't get access to
the `pre-receive` standard input so there's not much that I can do about this, that I know about.

## Usage

This should be used in combination with [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi):

```
$ heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git

$ cat .buildpacks
https://github.com/your-primary/buildpack-here
https://github.com/bjeanes/heroku-buildpack-runtime-git-sha
```

## License

[MIT](http://bjeanes.mit-license.org/)
