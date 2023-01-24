FROM docker.elastic.co/beats/filebeat:7.17.8              # イメージ指定
COPY filebeat.yml /usr/share/filebeat/filebeat.yml        # ホストのfilebeat.ymlをコンテナに上書き
USER root                                                 # コマンド実行の前にroot権限に変更
RUN chown root:filebeat /usr/share/filebeat/filebeat.yml  # 所有者をrootに、所有グループをfilebeatに変更
RUN chmod go-w /usr/share/filebeat/filebeat.yml           # 「自分以外の人」が「書き込めない」ように設定（http://www.damp.tottori-u.ac.jp/~ooshida/unix/chmod.html）
USER filebeat