ARG IMAGE_TAG
FROM webkitdev/tools:$IMAGE_TAG

SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

#--------------------------------------------------------------------
# Install MS Build Tools 2017
#--------------------------------------------------------------------

# FIXME: Currently we're installing the 15.7 toolset due to ongoing issues with 15.8 and later toolsets

RUN Install-VSBuildTools2017 -InstallationPath C:\MSVS -Workloads \
    Microsoft.VisualStudio.Workload.VCTools, \
    Microsoft.VisualStudio.Component.VC.Tools.14.14, \
    Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop, \
    Microsoft.VisualStudio.Component.Windows81SDK, \
    Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81;

#--------------------------------------------------------------------
# Install LLVM for Clang tooling support
#--------------------------------------------------------------------

ENV LLVM_VERSION 7.0.1

RUN Register-SystemPath -Path C:\LLVM\bin; \
    Install-LLVM -Version $env:LLVM_VERSION -InstallationPath C:\LLVM;