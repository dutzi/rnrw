# rnrw - react native react web

### how I setup this project

#### step 1 - start two seperate projects

```sh
cd ~/Documents
mkdir test-reactnative && cd test-reactnative
yo react-webapp # i went with sass and postcss
cd ~/Documents
mkdir test-reactnative2 && cd test-reactnative2
react-native init AwesomeProject
```

#### step 2 - merge the react native project into the web project

I copied everything from `AwesomeProject/` to `test-reactnative/` except for `package.json`  and the `node_modules` folder.

I then manually added the following to `test-reactnative/package.json` [diff](https://github.com/dutzi/rnrw/commit/dde1bdda8e1dee61b9d1f525fe1b77b2b1c6278a#diff-b9cfc7f2cdf78a7f4b91a753d10865a2R5):

```json
    "react": "^0.14.8",
    "react-native": "^0.24.1",
```

And copied both `react/` `react-native/` from `AwesomeProject/node_modules/` to `test-reactnative/node_modules/`.

I then deleted `test-reactnative/ios/build/` because I had errors when I tried running the RN project. I only got these errors because I ran it in the previous folder, so ignore this step if you don't get the same errors or can't find that folder.

Then I had to delete `.babelrc` and move the babel configurations to webpack's config file 280b27c79ca83d90a27833e04efe1dea7efea51d.

I concatenated both .gitignore files so git will ignore RN's files in the RW project.

At this point I was able to run both the RW project (`npm start`) and the RN one (`react-native run-ios`) from `test-reactnative/`.

