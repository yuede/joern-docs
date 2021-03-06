Notes for developers

## Modifying Grammar Definitions


When building joern, pre-generated versions of the parsers will be
used by default. This is fine in most cases, however, if you want to
make changes to the grammar definition files, you will need to
regenerate parsers using the antlr4 tool. For this purpose, it is
highly recommended to use the 'optimized' version of ANTLR4 to gain
maximum performance.

To build the optimized version of ANTLR4, do the following:

    $ git clone https://github.com/sharwell/antlr4/
    $ cd antlr4
    $ mvn -N install
    $ mvn -DskipTests=true -Dgpg.skip=true -Psonatype-oss-release -Djava6.home=$PATH_TO_JRE install

Next, copy the antlr4 tool and runtime to the following locations:

      $ cp tool/target/antlr4-$VERSION-complete.jar $JOERN/
      $ cp runtime/Java/target/antlr4-runtime-$VERSION-SNAPSHOT.jar $JOERN/lib

Parsers can then be regenerated by executing the script
'$JOERN/genParsers.sh'.