[![CustomBadge](https://img.shields.io/badge/TACC-CPLP-darkblue)](https://img.shields.io/badge/TACC-CPLP-blue)

# Core Portal Lifecycle Procedures

Detailed documentation on the complete lifecycle of a TACC ACI-WMA Core v2 Portal.

[Core Portal Lifecycle Procedures](https://tacc.github.io/Core-Portal-Lifecycle-Procedures/)

## Getting Started

To serve the file locally, we recommend using [Docker Desktop](https://www.docker.com/products/docker-desktop/) and the containerized markdown server [Madness](https://github.com/DannyBen/madness).

- Ensure _Docker Desktop_ is installed and running.
- Ensure _Madness_ is aliased and working: `> alias madness='docker run --rm -it -v $PWD:/docs -p 3000:3000 dannyben/madness'`
- Open a command prompt and navigate to the root folder of the markdown you want to serve (i.e. - `> cd /Users/<user_name>/code/markdown_src`).
- Start madness: `> madness`
- Open your browser to [`0.0.0.0:3000`](http://0.0.0.0:3000) (the default port for madness).
- View your live markdown.

_Note: Madness does not have a live reload feature. You will need to refresh your browser to see saved changes render on-screen._
