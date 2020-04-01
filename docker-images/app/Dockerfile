FROM roynirmal/pyndri:latest

RUN wget -O "stanford-corenlp-full-2017-06-09.zip" "http://nlp.stanford.edu/software/stanford-corenlp-full-2017-06-09.zip" \
  && apt-get install -y  unzip \
  && unzip "stanford-corenlp-full-2017-06-09.zip" \
  && rm "stanford-corenlp-full-2017-06-09.zip" 
  

RUN git clone https://github.com/microsoft/macaw.git \
  && cd macaw \
  && pip3 install setuptools \
  && pip3 install -r requirements.txt \
  && python3 setup.py install