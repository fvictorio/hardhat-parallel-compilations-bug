Reproduction for [hardhat#3722](https://github.com/NomicFoundation/hardhat/issues/3722) (or at least a similar problem).

To recreate the problem, you need to run `npx hardhat compile` in each of the projects at the same time and the compiler shouldn't be already downloaded.

```
# remove the compiler; this should work for linux but not for other operating systems
rm ~/.cache/hardhat-nodejs/compilers-v2/linux-amd64/solc-linux-amd64-v0.8.18+commit.87f61d96

# clean the projects
for i in hh*; do (cd $i && npx hardhat clean); done

# compile all the projects at the same time (notice the &)
for i in hh*; do (cd $i && npx hardhat compile)&; done
```
