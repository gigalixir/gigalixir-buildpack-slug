# gigalixir-buildpack-slug

For deploying a slug you have pre-built. A slug on gigalixir is often a release tarball generated by running

    MIX_ENV=prod mix release

But it could be any slug containing any sort of app, including non-elixir apps. For example, you could do something like this to create a slug that does not use releases.

    tar --dereference -z -cf app.tar.gz --exclude='.git' -C .

You then upload the slug somewhere and point to it in a `slug_buildpack.config` file that looks like this

    slug_url=https://example.com/app.tar.gz
