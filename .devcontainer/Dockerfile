FROM mcr.microsoft.com/devcontainers/base:jammy

ARG ERLANG_VERSION=27.1.3
ARG ELIXIR_VERSION=1.16.3
ARG ASDF_PATH=/home/vscode/.asdf

# dependency packages for erlang
RUN apt-get update && apt-get install -y build-essential autoconf m4 libncurses5-dev libwxgtk3.0-gtk3-dev libgl1-mesa-dev libglu1-mesa-dev libpng-dev libssh-dev unixodbc-dev xsltproc fop

USER vscode
RUN git clone https://github.com/asdf-vm/asdf.git ${ASDF_PATH} --branch v0.13.1
RUN echo '. ~/.asdf/asdf.sh' >> /home/vscode/.bashrc
RUN echo '. ~/.asdf/completions/asdf.bash' >> /home/vscode/.bashrc
ENV PATH=$PATH:~/.asdf/bin

RUN ${ASDF_PATH}/bin/asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git
RUN ${ASDF_PATH}/bin/asdf install erlang ${ERLANG_VERSION} && /home/vscode/.asdf/bin/asdf global erlang ${ERLANG_VERSION}
RUN ${ASDF_PATH}/bin/asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git
RUN ${ASDF_PATH}/bin/asdf install elixir ${ELIXIR_VERSION} && /home/vscode/.asdf/bin/asdf global elixir ${ELIXIR_VERSION}
