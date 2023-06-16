#ディストリビューションはdebian系を選択する。
FROM ubuntu:22.04

#シェルをbashにする。
SHELL ["/bin/bash","-c"]

#docker compose file経由で.envファイルの変数を参照する。
ARG GROUP_ID
ARG GROUP_NAME
ARG USER_ID
ARG USER_NAME
#一般ユーザを追加する。
RUN groupadd -g ${GROUP_ID} ${GROUP_NAME} \
 && useradd -m -s /bin/bash -u ${USER_ID} -g ${GROUP_ID} ${USER_NAME}

#x11-appsをインストールする。xyesなどが入っている。
RUN apt-get update && apt-get upgrade -y \
 && apt-get install x11-apps -y

#ユーザを切り替える。
USER ${USER_NAME}
#作業ディレクトリをホームに設定する。
WORKDIR ${WORK_DIR}

CMD ["/bin/bash"]