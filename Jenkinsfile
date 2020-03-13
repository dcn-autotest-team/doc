pipeline {
   agent { node { label "master"  //指定运行节点的标签
                  customWorkspace "${workspace}"  //指定运行工作目录(可选)
           }
   }

   options {
       timestamps()  //日志时间戳
	   skipDefaultCheckout()  //删除隐式checkout scm语句
	   disableConcurrentBuilds()  //禁止并行
	   timeout(time: 1, unit:'HOURS')  //流水线超时1h
   }

   stages {
       //下载代码
	   stage("GetCode"){   //阶段名称
	      steps{   //步骤
	         timeout(time: 5, unit:'MINUTES'){   //步骤超时时间
		        script{   //运行代码
			       println('获取代码')
			    }
		     }
	      }
	   }
	
	   //构建
	   stage("Build"){
	      steps{   //步骤
	         timeout(time: 20, unit:'MINUTES'){   //步骤超时时间
		        script{   //运行代码
			       println('应用打包')
			    }
		     }
	      }
	   }
	
	   //代码扫描
	   stage("CodeScan"){
	      steps{   //步骤
	         timeout(time: 30, unit:'MINUTES'){   //步骤超时时间
		        script{   //运行代码
			       println('代码扫描')
			    }
		     }
	      }
	   }
   }

   post {
      always {   //总是执行
         script{
	        println("always")
	     }
      }
   
      success {   //成功后执行
         script{
	        currentBuild.description = "\n 构建成功"
	     }
      }
   
      failure {   //失败后执行
         script{
	        currentBuild.description = "\n 构建失败"
	     }
      }
   
      aborted {   //取消后执行
         script{
	        currentBuild.description = "\n 构建取消"
	     }
      }
   }
}