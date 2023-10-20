![version](https://github.com/JamesGosnell42/RPITekton/assets/16072242/d40c6796-6f49-4eb5-81e7-8889fdf905d2)

For Windows Subsystem for Linux, follow the steps below to install Ko. If you are using MacOS, then it is suitable for you to install through Homebrew.
Determine the latest version of KO by visiting the KO GitHub releases page. Look for the highlighted version you want to install.

Set the necessary variables to install KO, replacing TODO with the version you identified. Adjust OS and ARCH according to your environment:

```
$ VERSION=TODO  # Choose the latest version (without v prefix)
$ OS=Linux       # Use Linux if you're using WSL2, or Darwin for MacOS
$ ARCH=x86_64    # Use the appropriate architecture for your computer (e.g., arm64, i386, s390x)
```
Download KO and its associated artifacts:

```
$ curl -sSfL "https://github.com/ko-build/ko/releases/download/v${VERSION}/ko_${VERSION}_${OS}_${ARCH}.tar.gz" > ko.tar.gz
$ curl -sSfL "https://github.com/ko-build/ko/releases/download/v${VERSION}/multiple.intoto.jsonl" > multiple.intoto.jsonl
```
IF you want to verify that Ko’s release, WHICH IS NOT NECESSARY, go to this page:
[ https://github.com/slsa-framework/slsa-verifier#installation ]. Follow the instructions and install SLSA and then into your command line type in:
```
slsa-verifier verify-artifact --provenance-path multiple.intoto.jsonl --source-uri github.com/ko-build/ko --source-tag "v${VERSION}" ko.tar.gz
Verified signature against tlog entry index 24413745 at URL: https://rekor.sigstore.dev/api/v1/log/entries/24296fb24b8ad77ab97a5263b5fa8f35789618348a39358b1f9470b0c31045effbbe5e23e77a5836
Verified build using builder "https://github.com/slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@refs/tags/v1.7.0" at commit 200db7243f02b5c0303e21d8ab8e3b4ad3a229d0
Verifying artifact /Users/batuhanapaydin/workspace/ko/ko.tar.gz: PASSED
```
And if all goes well, it should return this : ‘ PASSED: Verified SLSA provenance ‘

Extract KO and make it executable:
```
$ tar xzf ko.tar.gz ko
$ chmod +x ./ko
```

With these steps completed, you have successfully installed KO in your WSL environment. Now you need to add KO to your PATH from the command below: 
```
$ sudo export PATH="/root/ko/"
```
To check if you have ko, you can type ‘ ko version ‘ to verify the version and that ko is in your path.
