@startuml
skinparam defaultTextAlignment center

'■ユーザーリリース（青色）対象
node "fors-xx-apps" #0000FF
node "mors-xx-apps" #0000FF
node "jupyterhub" #0000FF
node "fors-minimal-notebook" #0000FF
node "fors-ml-notebook" #0000FF
node "fors-notebook" #0000FF
node "mors-minimal-notebook" #0000FF
node "mors-ml-notebook" #0000FF
node "mors-notebook" #0000FF
node "fors-airflow-worker" #0000FF
node "mors-airflow-worker" #0000FF

'■新分散（赤色）対象
node "ubi:python" #FF0000
node "smbc-base" #FF0000
node "spl-base" #FF0000
node "spl-build" #FF0000
node "spl-build-ci" #FF0000
node "python-38-with-postgresql" #FF0000
node "fors-base" #FF0000
node "mors-base" #FF0000
node "airflow" #FF0000
node "distributed-computing" #FF0000
node "fors-airflow-worker_base" #FF0000
node "mors-airflow-worker_base" #FF0000

'■注釈
note left of fors-xx-apps #ADD8E6
  <<ユーザーリリース>>
  ・xx-apps系
  ・notebook系
  ・airflow-worker系
end note

note right of ubi:python #FFB6C1
  <<新分散>>
  基盤コンポーネント
  開発環境基盤
end note

'■接続関係（元の定義を保持）
ubi:python --> smbc-base
smbc-base --> spl-base
smbc-base --> python-38-with-postgresql
python-38-with-postgresql --> jupyterhub
spl-base --> spl-build
spl-base --> fors-base
spl-base --> mors-base
spl-base --> distributed-computing
spl-base --> airflow
spl-build --> spl-build-ci
fors-base --> fors-xx-apps
fors-base --> mors-xx-apps
fors-base --> fors-minimal-notebook
fors-base --> fors-airflow-worker_base
fors-minimal-notebook --> fors-ml-notebook
fors-ml-notebook --> fors-notebook
fors-airflow-worker_base --> fors-airflow-worker
mors-base --> mors-minimal-notebook
mors-minimal-notebook --> mors-ml-notebook
mors-ml-notebook --> mors-notebook
mors-base --> mors-airflow-worker_base
mors-airflow-worker_base --> mors-airflow-worker
@enduml
