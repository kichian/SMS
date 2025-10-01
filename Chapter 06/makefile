CSOBJS = codesnippets.o
UPPEROBJS = upper.o

ifdef DEBUG
DEBUGFLGS = -g
else
DEBUGFLGS =
endif
LSTFLGS =

LDFLAGS = -lSystem -syslibroot `xcrun -sdk macosx --show-sdk-path` -e _start -arch arm64
all: codesnippets upper

%.o : %.s
	as $(DEBUGFLGS) $(LSTFLGS) $< -o $@
codesnippets: $(CSOBJS)
	ld -o codesnippets $(LDFLAGS) $(CSOBJS)

upper: $(UPPEROBJS)
	ld -o upper $(LDFLAGS) $(UPPEROBJS)

clean:
	rm -f *.o upper codesnippets
# command to generate docs using protoc-gen-doc
buf protoc \
-I "proto" \
-I "third_party/proto" \
--doc_out=./docs/api \
--doc_opt=./docs/protodoc-markdown.tmpl,proto-docs.md \
$(find "$(pwd)/proto" -maxdepth 5 -name '*.proto')
# go mod tidy

# move proto files to the right places
cp -r github.com/tharsis/evmos/* ./
rm -rf github.com
