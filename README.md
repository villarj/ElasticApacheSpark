# ElasticApacheSpark

Primero hay que asegurarse de que la biblioteca del conector Elasticserch-Hadoop esta instalado en el clúster Spark. Tiene que estar disponible en la misma ruta en cada uno de los nodos del cluster.

Para instalarlo hay que descargar el .jar (comprobar que versión se tiene de elasticsearch y apache spark)

http://mvnrepository.com/artifact/org.elasticsearch/elasticsearch-hadoop


Desafortunadente no hay una instalación pip elasticsearch-hadoop, por lo que hay que tener disponible el archivo binario y la ruta del jar. Si por ejemplo, esta ejecutando su codigo en un cuaderno de Jupyter o en un IDE como eclipse debe establecer un contexto de la siguiente forma:

import os
from pyspark import SparkContext, SparkConf

-- set environment variable PYSPARK_SUBMIT_ARGS

os.environ['PYSPARK_SUBMIT_ARGS'] = '--jars path/to/.jar pyspark-shell'

-- invoke SparkContext (using environment variable)

sc = SparkContext(appName="PythonSparkStreaming")

## Leer información de ElasticSearch usando el conector elasticsearc-hadoop.

es_read_conf = {# specify the node that we are sending data to (this should be the master)
"es.nodes" : 'localhost', # specify the port in case it is not the default port
"es.port" : '9200', # specify a resource in the form 'index/doc-type'
"es.resource" : 'testindex/testdoc'
}

Más información:

https://starsift.com/2018/01/18/integrating-pyspark-and-elasticsearch/
