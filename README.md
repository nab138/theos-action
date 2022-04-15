<h1 align="center">theos-action</h1>

Easily bootstraps Theos onto Actions runner, with caching for improved speed.

## Wait, what's Theos?

[Theos](https://github.com/theos/theos) is a cross-platform building suite for iOS and MacOS. It's mainly used for developing and compiling jailbroken iOS tweaks for the iPhone/iPad.

## Usage
Windows runners are not supported.

```yaml
- uses: beerpiss/theos-action@v1  # The v1 tag refers to the latest update of major version 1 (currently 1.3.0)
  with:
    # This is where Theos is stored, relative to the runner workspace.
    # Default: ${{ github.workspace }}/theos
    theos-dir: ''

    # This is where Theos will be git cloned from. It must be a Git repository.
    # Default: https://github.com/theos/theos
    theos-src: ''

    # The branch, tag or SHA to checkout Theos from.
    theos-ref: ''

    # This is where the Theos SDKs will be downloaded from. It must be a GitHub URL.
    # Default: https://github.com/theos/sdks
    # However, you'll probably want to set this manually if you want to compile using newer frameworks, like iOS 13 or 14.
    theos-sdks: ''

    # The branch, tag or SHA to get Theos SDKs from. 
    theos-sdks-ref: ''

    # Cache Theos and its SDKs. They are only fetched again when a new commit is pushed to their repos
    # Default: true
    cache: ''

    # Cache location for Theos
    # Default: /usr/local/opt/__theos_cache
    cache-dir-theos: ''

    # Cache location for SDKs
    # Default: /usr/local/opt/__theos_sdks_cache
    cache-dir-sdks: ''
    
```

## Example

See [this workflow](https://github.com/beerpiss/theos-action/blob/main/.github/workflows/build.yml) as an example of how to use this.

That workflow should work out-of-the-box for most Theos projects. Some tweaking may be required, but it's basically just copy-paste.

## Issues

Feel free to submit any issues or pull requests.

## License

This project is released under the [MIT License](LICENSE)
