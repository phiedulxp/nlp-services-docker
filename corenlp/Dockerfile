FROM java:8

ENV CORENLP_ARCHIVE_VERSION=2018-10-05
ENV CORENLP_ARCHIVE=stanford-corenlp-full-${CORENLP_ARCHIVE_VERSION}.zip \
  CORENLP_PATH=/corenlp

RUN wget http://nlp.stanford.edu/software/$CORENLP_ARCHIVE \
  && unzip $CORENLP_ARCHIVE \
  && mv $(basename ../$CORENLP_ARCHIVE .zip) $CORENLP_PATH \
  && rm $CORENLP_ARCHIVE

WORKDIR $CORENLP_PATH

RUN wget http://nlp.stanford.edu/software/stanford-english-corenlp-${CORENLP_ARCHIVE_VERSION}-models.jar
RUN wget http://nlp.stanford.edu/software/stanford-english-kbp-corenlp-${CORENLP_ARCHIVE_VERSION}-models.jar
RUN wget http://nlp.stanford.edu/software/stanford-chinese-corenlp-${CORENLP_ARCHIVE_VERSION}-models.jar

RUN export CLASSPATH="`find . -name '*.jar'`"

EXPOSE 9000
CMD ["java", "-mx6g", "-cp", "*", "edu.stanford.nlp.pipeline.StanfordCoreNLPServer", "9000"]
