# theos-action

_Use Theos in your GitHub Actions to build iOS tweaks, even without owning a Mac._

## Wait, what's Theos?

[Theos](https://github.com/theos/theos) is a cross-platform building suite for iOS and MacOS. It's mainly used for developing and compiling jailbroken iOS tweaks for the iPhone/iPad.

## What's new

v1.1: Added Procursus support for macOS 11 runners. This should shave off about 10-20 seconds of setup time.

v1: Initial release. Only MacOS support, and only supports 1 SDK repo (although you can just run it a few times or do it yourself). It works, but it is probably not very efficient.

## Usage

MAKE SURE YOU'RE USING THIS WITH A MACOS RUNNER!!! Linux support may be added if there is enough demand, but for now only Mac is supported.

```yaml
- uses: beerpiss/theos-action@v1  # The v1 tag refers to the latest update of major version 1 (currently 1.3.0)
  with:
    # This is where Theos is stored, relative to the runner workspace.
    # Default: ${{ github.workspace }}/theos
    theos-dir: ''
    # This is where Theos will be git cloned from. It must be a Git repository.
    # Default: https://github.com/theos/theos
    theos-src: ''
    # This is where the Theos SDKs will be downloaded from. It must be a GitHub URL.
    # Default: https://github.com/theos/sdks
    # However, you'll probably want to set this manually if you want to compile using newer frameworks, like iOS 13 or 14.
    theos-sdks: ''
    # Cache Theos and its SDKs. They are only fetched again when a new commit is pushed to their repos
    # Default: true
    cache:
    # Cache location for Theos
    # Default: /usr/local/opt/__theos_cache
    cache-dir-theos:
    # Cache location for SDKs
    # Default: /usr/local/opt/__theos_sdks_cache
    cache-dir-sdks:
    
```

## Example

See [this workflow](https://github.com/Randomblock1/FleetsBGone/blob/master/.github/workflows/build.yml) as an example of how to use this. It configures a custom SDK repository, uses GitHub Actions cache to speed up downloads (Theos and the SDKs are rarely updated), builds a tweak, and packages it up using GitHub Artifacts.

That workflow should work out-of-the-box for most Theos projects. Some tweaking may be required, but it's basically just copy-paste.

## Issues

Feel free to submit any issues or pull requests.

## License

This project is released under the [MIT License](LICENSE)
