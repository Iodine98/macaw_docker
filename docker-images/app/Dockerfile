FROM roynirmal/pyndri:latest

RUN pip3 install setuptools \
  && wget -O "stanford-corenlp-full-2017-06-09.zip" "http://nlp.stanford.edu/software/stanford-corenlp-full-2017-06-09.zip" \
  && apt-get install -y  unzip \
  && unzip "stanford-corenlp-full-2017-06-09.zip" \
  && rm "stanford-corenlp-full-2017-06-09.zip" 
  

RUN git clone --branch docker-tutorial https://github.com/roynirmal/macaw.git \
  && cd macaw \
  && pip3 install -r requirements.txt \
  && python3 setup.py install \
  && cd ..

RUN mkdir /data \
  && cd /data \
  && wget https://ciir.cs.umass.edu/downloads/wikipassageqa/WikiPassageQA.zip \
  && unzip WikiPassageQA.zip \
  && git clone https://github.com/roynirmal/convert2trectext.git \
  && cd convert2trectext \
  && python3 converter.py 

RUN /indri-5.11/buildindex/IndriBuildIndex -corpus.path=/data/input_file.txt -corpus.class=trectext -index=/data/index -memory=500m 


  
  