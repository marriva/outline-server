VERSION=1.4.1

.PHONY: all
all: bin/linux-x86_64/outline-ss-server bin/linux-arm64/outline-ss-server bin/macos-x86_64/outline-ss-server bin/macos-arm64/outline-ss-server

bin/linux-x86_64/outline-ss-server: OS=linux
bin/linux-x86_64/outline-ss-server: SHA256=b65028146c6df233b64cd940ff46ee75826abbe4ade12ebfa7933f0c4fe5878e

bin/linux-arm64/outline-ss-server: OS=linux
bin/linux-arm64/outline-ss-server: SHA256=0a8d2a2ceaa6d2dc7b1e2986445a2d92e389d48874afbc8bb0deae474e5e9001

bin/macos-x86_64/outline-ss-server: OS=macos
bin/macos-x86_64/outline-ss-server: SHA256=c37fb444b22b57f41028ae6fadbc355abafb9eed7e87b9e67f303e1f74d4703f

bin/macos-arm64/outline-ss-server: OS=macos
bin/macos-arm64/outline-ss-server: SHA256=239256ef7606ebfa1787d7afcad2dd559e2165a76fedc7bf47cfddfc1490d852

TEMPFILE := $(shell mktemp)
bin/%/outline-ss-server:
	node ../../src/build/download_file.mjs --url="https://github.com/marriva/outline-ss-server/releases/download/v$(VERSION)/outline-ss-server_$(VERSION)_$(OS)_$(ARCH).tar.gz" --out="$(TEMPFILE)" --sha256=$(SHA256)
	mkdir -p "$(dir $@)"
	tar -zx -f "$(TEMPFILE)" -C "$(dir $@)" "$(notdir $@)"
	chmod +x "$@"
	rm -f $(TEMPFILE)

.PHONY: clean
clean:
	rm -rf bin
