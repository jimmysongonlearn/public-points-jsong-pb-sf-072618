
# Public Points


```python
# Getting the public point from a secret
from ecc import G

secret = 999
point = secret*G
print(point)
```

### Try it

#### Get the public point where the scalar is the following:
```
7, 1485, 2**128, 2**240+2**31
```


```python
from ecc import G

secrets = (7, 1485, 2**128, 2**240+2**31)

# iterate over secrets
for secret in secrets:
    # get the public point
    print(secret*G)
```

### Test Driven Exercise

It's your turn to write a test now. Write the test below checking for the group order using the comments as a guide.


```python
from helper import run_test
from unittest import TestCase
from ecc import S256Point, G

class S256Test(TestCase):

    def test_pubpoint(self):
        # write a test that tests the public point for the following
        points = (
            # secret, x, y
            (7, 0x5cbdf0646e5db4eaa398f365f2ea7a0e3d419b7e0330e39ce92bddedcac4f9bc, 0x6aebca40ba255960a3178d6d861a54dba813d0b813fde7b5a5082628087264da),
            (1485, 0xc982196a7466fbbbb0e27a940b6af926c1a74d5ad07128c82824a11b5398afda, 0x7a91f9eae64438afb9ce6448a1c133db2d8fb9254e4546b6f001637d50901f55),
            (2**128, 0x8f68b9d2f63b5f339239c1ad981f162ee88c5678723ea3351b7b444c9ec4c0da, 0x662a9f2dba063986de1d90c2b6be215dbbea2cfe95510bfdf23cbf79501fff82),
            (2**240+2**31, 0x9577ff57c8234558f293df502ca4f09cbc65a6572c842b39b366f21717945116, 0x10b49c67fa9365ad7b90dab070be339a1daf9052373ec30ffae4f72d5e66d053),
        )

        # iterate over points
        for secret, x, y in points:
            # initialize the secp256k1 point (S256Point)
            point = S256Point(x, y)
            # check that the secret*G is the same as the point
            self.assertEqual(secret*G, point)
```

### Run your tests!

See whether your test works by running the cell below (remember to run the cell above too!).


```python
run_test(S256Test('test_pubpoint'))
```
