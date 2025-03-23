FROM dockerhub.docker.zooxlabs.com/ubuntu:noble
RUN apt-get update -y && apt-get install -y wget sudo lsb-release gpg software-properties-common git cmake ninja-build
RUN wget https://apt.llvm.org/llvm.sh &&  \ 
    chmod +x llvm.sh && \
    ./llvm.sh 17 all &&  \
    sudo update-alternatives --install /usr/bin/cc cc /usr/bin/clang-17 30 && \
    sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++-17 30 && \
    git clone --depth=1 --single-branch https://github.com/google/benchmark.git && \
    cd benchmark && cmake -E make_directory "build" && \
    cmake -DBENCHMARK_DOWNLOAD_DEPENDENCIES=on -DCMAKE_BUILD_TYPE=Release -S . -B "build" && \
    cmake --build "build" --config Release && \
    sudo cmake --build "build" --config Release --target install

ENTRYPOINT ["bash"]
