#!groovy
@Library('roboshop-shared-library')_


def configMap=[
    application:"nodejsVM" ,
    component:"catalogue"
]
if( ! env.BRANCH_NAME.equalsIgnoreCase('main')){
   pipelineDecission.decidePipeline(configMap)
}
else{
   echo "thi is prod pipeline"
}
