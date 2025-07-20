TEMPLATE = org.freedesktop.Platform.VulkanLayer.lsfgvk.yml.in
OUTPUT = org.freedesktop.Platform.VulkanLayer.lsfgvk.yml

RUNTIME_VERSION ?= 24.08

ifeq ($(RUNTIME_VERSION),23.08)
LLVM_VERSION = llvm18
else ifeq ($(RUNTIME_VERSION),24.08)
LLVM_VERSION = llvm20
else
$(error Invalid RUNTIME_VERSION: $(RUNTIME_VERSION))
endif

all: $(OUTPUT)

$(OUTPUT): $(TEMPLATE)
	@sed -e 's/{{RUNTIME_VERSION}}/$(RUNTIME_VERSION)/g' \
		-e 's/{{LLVM_VERSION}}/$(LLVM_VERSION)/g' \
		$(TEMPLATE) > $(OUTPUT)

clean:
	@rm -f $(OUTPUT)

help:
	@echo "Usage: make [RUNTIME_VERSION=<version>]"
	@echo "  RUNTIME_VERSION=23.08  Generate manifest for runtime 23.08"
	@echo "  RUNTIME_VERSION=24.08  Generate manifest for runtime 24.08"

.PHONY: all clean help
