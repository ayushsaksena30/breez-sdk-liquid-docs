## Steps to compile the snippets locally
1. Build a react native package
  - By running the publish-all-platforms CI in the breez-sdk-liquid repository (use dummy binaries)
2. Download the react-native-{VERSION} artifact 
3. Unzip the artifact and put the `breez-sdk-liquid-react-native.tgz` file in the `snippets/react-native/packages` folder
4. Run `yarn` to install the package.
5. Happy coding

The first few steps above can be done on the CLI with

```shell
mkdir packages
cd packages

wget $(npm view @breeztech/breez-sdk-liquid-react-native dist.tarball)
tar xvfz *.tgz
cp package/breez-sdk-liquid-react-native.tgz ../packages/
rm -rf package
cd ..
```

To use locally-generated bindings:
- Replace `"@breeztech/breez-sdk-liquid-react-native": "^0.1.3-rc2"` in `package.json` with
  - `"@breeztech/breez-sdk-liquid-react-native": "file:./packages/breez-sdk-liquid-react-native.tgz"`
- run `yarn`

## Nix

```
yarn add @breeztech/breez-sdk-liquid-react-native

nix develop

yarn
tsc
yarn run lint
```