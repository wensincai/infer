# Copyright (c) 2016 - present Facebook, Inc.
# All rights reserved.
#
# This source code is licensed under the BSD style license found in the
# LICENSE file in the root directory of this source tree. An additional grant
# of patent rights can be found in the PATENTS file in the same directory.

TESTS_DIR = ../..

ANALYZER = infer
SOURCES = $(wildcard src/infer/*.java)
OBJECTS = $(patsubst %.java,ant_out/%.class,$(SOURCES))
INFERPRINT_OPTIONS = --issues-tests

include $(TESTS_DIR)/java.make
include $(TESTS_DIR)/base.make

$(OBJECTS): $(SOURCES)
	ant

infer-out/report.json: $(INFER_BIN) $(SOURCES)
	$(call silent_on_success,\
	  $(INFER_BIN) -a $(ANALYZER) --project-root $(TESTS_DIR) --inferconfig-home . -- ant)

clean:
	ant clean
