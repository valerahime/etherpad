# Valeracore Etherpad

A very basic repo to rebuild the [default Etherpad Docker image](https://hub.docker.com/r/etherpad/etherpad) with a [list of plugins](#plugins).

Nothing is saved directly here (though I might use my own `settings.json` eventually). It's literally just the [workflow file](./.github/workflows/docker-publish.yml), which is pretty close to the default build/push workflow. This one does the following every day at 4 AM:

1. Check if the parent image has updated, via [twiddler/is-my-docker-parent-image-out-of-date](https://github.com/twiddler/is-my-docker-parent-image-out-of-date).
  1. If not, skip the rest of the workflow.
2. Checkout the [main Etherpad repo](https://github.com/ether/etherpad-lite).
3. Install the necessary Docker tools.
4. Builds and pushes the new image to this [repo's package registry](https://github.com/valerahime/etherpad/pkgs/container/etherpad).

The difference is the `ETHERPAD_PLUGINS` build arg and environment variable, which installs the plugins listed below. Note that this doesn't *enable* the plugins for some reason; you still have to go into the `/admin` page and enable them manually.

## Plugins

This list is subject to change, check out the [workflow file](./.github/workflows/docker-publish.yml) for the current iteration.

- ep_align
- ep_headings2
- ep_table_of_contents
- ep_font_size
- ep_markdown
- ep_cursortrace
- ep_font_color
- ep_set_title_on_pad
- ep_comments_page
- ep_font_family
- ep_hide_referrer
