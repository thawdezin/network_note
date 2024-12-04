# network_note

change mac address in macOS -> ``` sudo ifconfig en0 ether 02:1A:2B:3C:4D:5E ``` 

# Save this as test_env.sh

chmod +x test_env.sh

```
#!/bin/bash

# Test if ANDROID_NDK is set
if [ -z "$ANDROID_NDK" ]; then
  echo "ANDROID_NDK is not set. Please set the path to your Android NDK."
  exit 1
else
  echo "ANDROID_NDK is set to: $ANDROID_NDK"
fi

# Test if API_VERSION is set
if [ -z "$API_VERSION" ]; then
  echo "API_VERSION is not set. Please set the Android API version (between 21 and 30)."
  exit 1
else
  echo "API_VERSION is set to: $API_VERSION"
fi

# Test if ANDROID_ABI is set
if [ -z "$ANDROID_ABI" ]; then
  echo "ANDROID_ABI is not set. Please set the target architecture (arm64-v8a, armeabi-v7a, x86, x86_64)."
  exit 1
else
  echo "ANDROID_ABI is set to: $ANDROID_ABI"
fi

# Test if LIBPCAP_DIR is set
if [ -z "$LIBPCAP_DIR" ]; then
  echo "LIBPCAP_DIR is not set. Please set the path to the compiled libpcap directory."
  exit 1
else
  echo "LIBPCAP_DIR is set to: $LIBPCAP_DIR"
  
  # Check if the libpcap.a exists in the specified directory
  if [ ! -f "$LIBPCAP_DIR/$ANDROID_ABI/$API_VERSION/libpcap.a" ]; then
    echo "libpcap.a not found in $LIBPCAP_DIR/$ANDROID_ABI/$API_VERSION."
    exit 1
  else
    echo "libpcap.a found at $LIBPCAP_DIR/$ANDROID_ABI/$API_VERSION/libpcap.a"
  fi
fi

echo "All variables are set correctly and paths exist."

```

ဒါပြီးရင် လိုတာကို လိုက်ထည့်

### To install

```brew install cmake git make```

``` brew install libpcap ```

``` brew install ccache ```
``` brew install autoconf ```

### တစ်ခုခု Install ပြီးတိုင်း ဒီလိုလေးတွေ လိုက်လုပ်
If you need to have libpcap first in your PATH, run:
  ```echo 'export PATH="/opt/homebrew/opt/libpcap/bin:$PATH"' >> ~/.zshrc```

For compilers to find libpcap you may need to set:
  ```export LDFLAGS="-L/opt/homebrew/opt/libpcap/lib"```
  ```export CPPFLAGS="-I/opt/homebrew/opt/libpcap/include"```


# libpcap ကို ./build.sh နဲ့ install လုပ်



