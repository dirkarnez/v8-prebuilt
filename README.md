v8-prebuilt
===========
```
 git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git

install_v8() {
  if [ -d ${V8EVAL_ROOT}/v8 ]; then
    return 0
  fi

  cd ${V8EVAL_ROOT}
  fetch v8
  cd v8
  git checkout 7.1.177
  gclient sync
  if [ ${PLATFORM} = "Linux" ]; then
    ./build/install-build-deps.sh
  fi
  tools/dev/v8gen.py x64.release -- v8_use_snapshot=false v8_enable_i18n_support=false
  ninja -v -C out.gn/x64.release
}

```
