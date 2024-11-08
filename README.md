# fused-gtest

> [!WARNING]
> Unofficial single-source single-header for the googletest library.

Google [removed support](https://github.com/google/googletest/commit/47f819c3) for generating a single-file googletest with version 1.12.
This repository provides unofficial fused versions for releases after 1.11.

1. Download the version you want from [`_generated`](https://github.com/cwpearson/gtest-fuser/tree/master/_generated)
2. Provide your own main function, something like this:

```bash
cat << 'EOF' >> main.cpp
#include <gtest/gtest.h>
int main(int argc, char **argv) {
  printf("Running main() from %s\n", __FILE__);
  testing::InitGoogleTest(&argc, argv);
  return RUN_ALL_TESTS();
}
EOF
```

3. Compile together:

```bash
g++ --std=c++14 -I gtest-<version> main.cpp gtest-<version>/gtest-all.cc
```

## Legal

Users should take care to respect the respective googletest licences [(current version)](https://github.com/google/googletest/blob/main/LICENSE).
The license for each release is included in this repository as well.
