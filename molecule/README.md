1. Create dirs to be mounted into container:

        # mkdir -p /tmp/gentoo-molecule/{gentoo-repo,binpkgs}

    First will hold the synchronized Gentoo repository, second – built packaghes. Eselect-repository needs lxml, no point in building it all the time

2. Install `jmespath`
