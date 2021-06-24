# containers
Collection of useful and reusable containers for bioinformatics pipelines

## Contents

### bwakit/0.7.15-bwa-0.7.17

[bwakit](https://github.com/lh3/bwa/tree/master/bwakit) is a self-consistent installation-free package of scripts and precompiled binaries, providing an end-to-end solution to read mapping.

As of June 2021, [bwakit releases on SourceForge](https://sourceforge.net/projects/bio-bwa/files/bwakit/) are behind the [bwa repository on GitHub](https://github.com/lh3/bwa). Therefore we provide bwakit v0.7.15 updated with the contents of the directory bwakit from bwa v0.7.17. Note that this does not actually update the included version of the bwa binary, but it does fix the GRCh38 download URL.

Usage:

```
docker pull ghcr.io/gandallab/bwakit:0.7.15-bwa-0.7.17
```

## Maintaining

```
docker build -t ghcr.io/gandallab/bwakit:0.7.15-bwa-0.7.17 -t ghcr.io/gandallab/bwakit:latest .

docker push -a ghcr.io/gandallab/bwakit
```

With `LABEL org.opencontainers.image.source=https://github.com/gandallab/containers` in the Dockerfile the package was automatically tied to this repository. Had to manually change package visibility to public. See [Working with the Container registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry) for how to authenticate to ghcr.io.

## See also

- [BioContainers](https://biocontainers.pro/) for containers of every package on BioConda.