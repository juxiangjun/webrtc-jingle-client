vars = {
  # Use this googlecode_url variable only if there is an internal mirror for it.
  # If you do not know, use the full path while defining your new deps entry.
  "googlecode_url": "http://%s.googlecode.com/svn",
  "chromium_trunk" : "https://src.chromium.org/viewvc/chrome/trunk",
  "chromium_git_url" : "https://chromium.googlesource.com/",
  "github_luke_url" : "https://www.github.com/lukeweber",
  "chromium_revision": "182149",

  # External resources like video and audio files used for testing purposes.
  # Downloaded on demand when needed.
  "webrtc_resources_revision": "9",
}

# NOTE: Prefer revision numbers to tags for svn deps. Use http rather than
# https; the latter can cause problems for users behind proxies.
deps = {
  "trunk/testing":
    Var("chromium_trunk") + "/src/testing@" + Var("chromium_revision")
}

deps_os = {
    "ios" : {
          "trunk/third_party/xmppframework":
            "https://github.com/lukeweber/XMPPFramework.git",
    }
}

hooks = [
  {
    # Create a supplement.gypi file under trunk/src.  This file will be picked
    # up by gyp and used to enable the standalone build.
    "pattern": ".",
    "action": ["python", "trunk/tools/create_supplement_gypi.py", "trunk/client/supplement.gypi"],
  },
  {
    # A change to a .gyp, .gypi, or to GYP itself should run the generator.
    "pattern": ".",
    "action": ["python", "trunk/build/gyp_chromium", "--depth=trunk", "trunk/webrtcjingle.gyp"],
  },
]
