my_dag = DAG("my_first_dag", start_date=pendulum.datetime(2023, 3, 3, tz="UTC"),
             schedule="@daily", catchup=False)
op = EmptyOperator(task_id="empty_task", dag=my_first_dag)
bash_task = BashOperator(
    dag=my_first_dag,
    task_id="bash_task",
    bash_command="echo \"here is the message: '$message'\"",
    env={"message": '{{ dag_run.conf["message"] if dag_run else "" }}'},
)
op >> bash_task
