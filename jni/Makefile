# Build the native component of the PocketSphinx library for JNI Bindings.
TARGET_LIBRARY = libpocketsphinx_jni.so

# You MUST change this to the absolute path of the directory containing
# sphinxbase and pocketsphinx source code.
SPHINX_PATH := /Users/baback/Documents/dev/alexa-build/pocketsphinx

CC = gcc
CFLAGS = -fPIC -c -g -O2 -Wall -Wno-unused-function -Wno-logical-op-parentheses
SHARED_LINKFLAGS = -shared -lm -lc -ldl -lpthread 
DEFS = -DHAVE_CONFIG_H
LOCAL_C_INCLUDES=-I$(SPHINX_PATH)/sphinxbase/include -I$(SPHINX_PATH)/pocketsphinx/include -I$(JAVA_HOME)/include

UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Linux)
    LOCAL_C_INCLUDES += -I$(JAVA_HOME)/include/linux
    SHARED_LINKFLAGS += -Wl,-no-whole-archive -Wl,-soname,$(TARGET_LIBRARY), -o $(TARGET_LIBRARY)
endif
ifeq ($(UNAME_S),Darwin)
    LOCAL_C_INCLUDES += -I$(JAVA_HOME)/include/darwin
    SHARED_LINKFLAGS += -Wl,-all_load -Wl,-install_name,$(TARGET_LIBRARY), -o $(TARGET_LIBRARY)
endif

COMPILE = $(CC) $(DEFS) $(LOCAL_C_INCLUDES) $(CFLAGS)
SHARED_LINK = $(CC) $(SHARED_LINKFLAGS)

#libsphinxutil library
SPHINXUTIL_PATH=$(SPHINX_PATH)/sphinxbase/src/libsphinxbase/util

SPHINXUTIL_SRC := \
  $(SPHINXUTIL_PATH)/bio.c \
  $(SPHINXUTIL_PATH)/bitarr.c \
  $(SPHINXUTIL_PATH)/bitvec.c \
  $(SPHINXUTIL_PATH)/case.c \
  $(SPHINXUTIL_PATH)/ckd_alloc.c \
  $(SPHINXUTIL_PATH)/cmd_ln.c \
  $(SPHINXUTIL_PATH)/dtoa.c \
  $(SPHINXUTIL_PATH)/err.c \
  $(SPHINXUTIL_PATH)/filename.c \
  $(SPHINXUTIL_PATH)/genrand.c \
  $(SPHINXUTIL_PATH)/glist.c \
  $(SPHINXUTIL_PATH)/hash_table.c \
  $(SPHINXUTIL_PATH)/heap.c \
  $(SPHINXUTIL_PATH)/listelem_alloc.c \
  $(SPHINXUTIL_PATH)/logmath.c \
  $(SPHINXUTIL_PATH)/matrix.c \
  $(SPHINXUTIL_PATH)/mmio.c \
  $(SPHINXUTIL_PATH)/pio.c \
  $(SPHINXUTIL_PATH)/profile.c \
  $(SPHINXUTIL_PATH)/priority_queue.c \
  $(SPHINXUTIL_PATH)/sbthread.c \
  $(SPHINXUTIL_PATH)/strfuncs.c \
  $(SPHINXUTIL_PATH)/slamch.c \
  $(SPHINXUTIL_PATH)/slapack_lite.c \
  $(SPHINXUTIL_PATH)/blas_lite.c \
  $(SPHINXUTIL_PATH)/f2c_lite.c

SPHINXUTIL_OBJ=$(SPHINXUTIL_SRC:.c=.o)

libsphinxutil: $(SPHINXUTIL_SRC) $(SPHINXUTIL_OBJ)
	ar cru libsphinxutil.a $(SPHINXUTIL_OBJ)
	ranlib libsphinxutil.a


#libsphinxfe library
SPHINXFE_PATH := $(SPHINX_PATH)/sphinxbase/src/libsphinxbase/fe

SPHINXFE_SRC := \
  $(SPHINXFE_PATH)/fe_noise.c \
  $(SPHINXFE_PATH)/fe_prespch_buf.c \
  $(SPHINXFE_PATH)/fe_interface.c \
  $(SPHINXFE_PATH)/fe_sigproc.c \
  $(SPHINXFE_PATH)/fe_warp_affine.c \
  $(SPHINXFE_PATH)/fe_warp.c \
  $(SPHINXFE_PATH)/fe_warp_inverse_linear.c \
  $(SPHINXFE_PATH)/fe_warp_piecewise_linear.c \
  $(SPHINXFE_PATH)/fixlog.c

SPHINXFE_OBJ=$(SPHINXFE_SRC:.c=.o)

libsphinxfe: $(SPHINXFE_SRC) $(SPHINXFE_OBJ)
	ar cru libsphinxfe.a $(SPHINXFE_OBJ)
	ranlib libsphinxfe.a


#libsphinxfeat library
SPHINXFEAT_PATH := $(SPHINX_PATH)/sphinxbase/src/libsphinxbase/feat

SPHINXFEAT_SRC := \
  $(SPHINXFEAT_PATH)/agc.c \
  $(SPHINXFEAT_PATH)/cmn.c \
  $(SPHINXFEAT_PATH)/cmn_prior.c \
  $(SPHINXFEAT_PATH)/feat.c \
  $(SPHINXFEAT_PATH)/lda.c

SPHINXFEAT_OBJ=$(SPHINXFEAT_SRC:.c=.o)

libsphinxfeat: $(SPHINXFEAT_SRC) $(SPHINXFEAT_OBJ)
	ar cru libsphinxfeat.a $(SPHINXFEAT_OBJ)
	ranlib libsphinxfeat.a

#libsphinxlm library
SPHINXLM_PATH := $(SPHINX_PATH)/sphinxbase/src/libsphinxbase/lm

SPHINXLM_SRC := \
  $(SPHINXLM_PATH)/fsg_model.c \
  $(SPHINXLM_PATH)/jsgf.c \
  $(SPHINXLM_PATH)/jsgf_parser.c \
  $(SPHINXLM_PATH)/jsgf_scanner.c \
  $(SPHINXLM_PATH)/lm_trie.c \
  $(SPHINXLM_PATH)/lm_trie_quant.c \
  $(SPHINXLM_PATH)/ngram_model_trie.c \
  $(SPHINXLM_PATH)/ngram_model_set.c \
  $(SPHINXLM_PATH)/ngram_model.c \
  $(SPHINXLM_PATH)/ngrams_raw.c

SPHINXLM_OBJ=$(SPHINXLM_SRC:.c=.o)

libsphinxlm: $(SPHINXLM_SRC) $(SPHINXLM_OBJ)
	ar cru libsphinxlm.a $(SPHINXLM_OBJ)
	ranlib libsphinxlm.a

#libsphinxlm library
POCKETSPHINX_PATH := $(SPHINX_PATH)/pocketsphinx/src/libpocketsphinx

POCKETSPHINX_SRC := \
  $(POCKETSPHINX_PATH)/acmod.c     \
  $(POCKETSPHINX_PATH)/allphone_search.c \
  $(POCKETSPHINX_PATH)/bin_mdef.c    \
  $(POCKETSPHINX_PATH)/blkarray_list.c   \
  $(POCKETSPHINX_PATH)/dict.c     \
  $(POCKETSPHINX_PATH)/dict2pid.c    \
  $(POCKETSPHINX_PATH)/fsg_history.c   \
  $(POCKETSPHINX_PATH)/fsg_lextree.c   \
  $(POCKETSPHINX_PATH)/fsg_search.c   \
  $(POCKETSPHINX_PATH)/kws_detections.c \
  $(POCKETSPHINX_PATH)/kws_search.c   \
  $(POCKETSPHINX_PATH)/hmm.c     \
  $(POCKETSPHINX_PATH)/mdef.c     \
  $(POCKETSPHINX_PATH)/ms_gauden.c    \
  $(POCKETSPHINX_PATH)/ms_mgau.c    \
  $(POCKETSPHINX_PATH)/ms_senone.c    \
  $(POCKETSPHINX_PATH)/ngram_search.c   \
  $(POCKETSPHINX_PATH)/ngram_search_fwdtree.c \
  $(POCKETSPHINX_PATH)/ngram_search_fwdflat.c \
  $(POCKETSPHINX_PATH)/phone_loop_search.c  \
  $(POCKETSPHINX_PATH)/pocketsphinx.c \
  $(POCKETSPHINX_PATH)/ps_lattice.c   \
  $(POCKETSPHINX_PATH)/ps_mllr.c    \
  $(POCKETSPHINX_PATH)/ptm_mgau.c    \
  $(POCKETSPHINX_PATH)/s2_semi_mgau.c   \
  $(POCKETSPHINX_PATH)/tmat.c     \
  $(POCKETSPHINX_PATH)/vector.c

POCKETSPHINX_OBJ=$(POCKETSPHINX_SRC:.c=.o)

libpocketsphinx: $(POCKETSPHINX_SRC) $(POCKETSPHINX_OBJ)
	ar cru libpocketsphinx.a $(POCKETSPHINX_OBJ)
	ranlib libpocketsphinx.a

# libsphinxbase_wrap
sphinxbase_wrap.o: sphinxbase_wrap.c
	$(COMPILE) -DSWIG_NOINCLUDE sphinxbase_wrap.c -o sphinxbase_wrap.o

# libpocketsphinx_wrap
pocketsphinx_wrap.o: pocketsphinx_wrap.c
	$(COMPILE) pocketsphinx_wrap.c -o pocketsphinx_wrap.o

# Create the dynamic library wrapper
$(TARGET_LIBRARY): libsphinxutil libsphinxfe libsphinxfeat libsphinxlm libpocketsphinx sphinxbase_wrap.o pocketsphinx_wrap.o
	$(SHARED_LINK) libpocketsphinx.a libsphinxlm.a libsphinxfeat.a libsphinxfe.a libsphinxutil.a pocketsphinx_wrap.o sphinxbase_wrap.o

all: $(TARGET_LIBRARY)

.c.o:
	$(COMPILE) $< -o $@

clean_objs: 
	rm $(SPHINXUTIL_OBJ)
	rm $(SPHINXFE_OBJ) 
	rm $(SPHINXFEAT_OBJ) 
	rm $(SPHINXLM_OBJ) 
	rm $(POCKETSPHINX_OBJ) 
	rm pocketsphinx_wrap.o 
	rm sphinxbase_wrap.o

clean: clean_objs
	rm libsphinxutil.a
	rm libsphinxfe.a
	rm libsphinxfeat.a
	rm libsphinxlm.a
	rm libpocketsphinx.a
	rm libsphinxbase_wrap.a
	rm libpocketsphinx_wrap.a
	rm $(TARGET_LIBRARY)
	
