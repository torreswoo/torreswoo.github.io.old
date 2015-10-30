# Spark
- 소스코드 참고 : http://homepage.cs.latrobe.edu.au/zhe/
- Spark Environment : Standalone(HDFS없이도가능) / YARN / Mesos
- 아키텍쳐

---

- Package Build & pre-build
- Shell in local mode
- Run Spark Shell
   - SPARK_PRINT_LAUNCH_COMMAND=1 : 약간 디버깅모드로
   - -i init.script / :load init.script : 초기에 로딩시킬 스크립트를 설정할떄사용
- Web UI : localhost:4040/

- RDD (Resilient Distributed Dataset)
   - read-only collection of objects partitioned across a set of machines that can be rebuilt if a partition is lost
   - read-only : immutable / parallelism ->분산처리 , 오랫동안캐싱가능
   - Transformation for change : 데이터복사반복->성능떨어짐  / Laziness로극복
   - Distributed : partitioned
   - Resilient : rebuilt / data lineage
