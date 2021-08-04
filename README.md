# ASTVerifierReproducer
Reproducer for https://github.com/apple/swift/pull/32343

```
% /Library/Developer/Toolchains/swift-DEVELOPMENT-SNAPSHOT-2021-07-24-a.xctoolchain/usr/bin/swift build
GenericTypeParamDecl has incorrect depth
Please submit a bug report (https://swift.org/contributing/#reporting-bugs) and include the project and the crash backtrace.
Stack dump:
0.	Program arguments: /Library/Developer/Toolchains/swift-DEVELOPMENT-SNAPSHOT-2021-07-24-a.xctoolchain/usr/bin/swift-frontend -frontend -merge-modules -emit-module /Users/___/ASTVerifierReproducer/.build/x86_64-apple-macosx/debug/ASTVerifierReproducer.build/autodiff2~partial.swiftmodule -parse-as-library -disable-diagnostic-passes -disable-sil-perf-optzns -target x86_64-apple-macosx10.10 -enable-objc-interop -sdk /Applications/Xcode-beta.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX12.0.sdk -I /Users/___/ASTVerifierReproducer/.build/x86_64-apple-macosx/debug -I /Applications/Xcode-beta.app/Contents/Developer/Platforms/MacOSX.platform/Developer/usr/lib -F /Applications/Xcode-beta.app/Contents/Developer/Platforms/MacOSX.platform/Developer/Library/Frameworks -color-diagnostics -enable-testing -g -module-cache-path /Users/___/ASTVerifierReproducer/.build/x86_64-apple-macosx/debug/ModuleCache -swift-version 5 -Onone -D SWIFT_PACKAGE -D DEBUG -new-driver-path /Library/Developer/Toolchains/swift-DEVELOPMENT-SNAPSHOT-2021-07-24-a.xctoolchain/usr/bin/swift-driver -entry-point-function-name ASTVerifierReproducer_main -resource-dir /Library/Developer/Toolchains/swift-DEVELOPMENT-SNAPSHOT-2021-07-24-a.xctoolchain/usr/lib/swift -enable-anonymous-context-mangled-names -module-name ASTVerifierReproducer -target-sdk-version 12.0.0 -emit-module-doc-path /Users/___/ASTVerifierReproducer/.build/x86_64-apple-macosx/debug/ASTVerifierReproducer.swiftdoc -emit-module-source-info-path /Users/___/ASTVerifierReproducer/.build/x86_64-apple-macosx/debug/ASTVerifierReproducer.swiftsourceinfo -o /Users/___/ASTVerifierReproducer/.build/x86_64-apple-macosx/debug/ASTVerifierReproducer.swiftmodule
1.	Apple Swift version 5.6-dev (LLVM 294fb71bbb58dbf, Swift b6af50d7df4ac93)
2.	
3.	While verifying GenericTypeParamDecl 'τ_1_0' (in module 'ASTVerifierReproducer')
Stack dump without symbol names (ensure you have llvm-symbolizer in your PATH or set the environment var `LLVM_SYMBOLIZER_PATH` to point to it):
0  swift-frontend           0x0000000113c5b4c7 llvm::sys::PrintStackTrace(llvm::raw_ostream&, int) + 39
1  swift-frontend           0x0000000113c5a6e5 llvm::sys::RunSignalHandlers() + 85
2  swift-frontend           0x0000000113c5bd16 SignalHandler(int) + 278
3  libsystem_platform.dylib 0x00007fff204b9d7d _sigtramp + 29
4  libsystem_platform.dylib 000000000000000000 _sigtramp + 18446603339974337184
5  libsystem_c.dylib        0x00007fff203c9406 abort + 125
6  swift-frontend           0x0000000114150879 (anonymous namespace)::Verifier::walkToDeclPost(swift::Decl*) (.cold.6) + 25
7  swift-frontend           0x00000001103670a3 (anonymous namespace)::Verifier::walkToDeclPost(swift::Decl*) + 5859
8  swift-frontend           0x000000011036ec69 (anonymous namespace)::Traversal::doIt(swift::Decl*) + 121
9  swift-frontend           0x000000011036ebdb swift::Decl::walk(swift::ASTWalker&) + 27
10 swift-frontend           0x0000000110359e1a swift::verify(swift::Decl*) + 218
11 swift-frontend           0x000000010f83a7f6 swift::ModuleFile::verify() const + 118
12 swift-frontend           0x000000010f8ac3c8 swift::SerializedModuleLoaderBase::verifyAllModules() + 40
13 swift-frontend           0x00000001102bc0ba swift::ASTContext::verifyAllLoadedModules() const + 90
14 swift-frontend           0x000000010f2c6555 performEndOfPipelineActions(swift::CompilerInstance&) + 677
15 swift-frontend           0x000000010f2c2cec swift::performFrontend(llvm::ArrayRef<char const*>, char const*, void*, swift::FrontendObserver*) + 10396
16 swift-frontend           0x000000010f269cd2 swift::mainEntry(int, char const**) + 546
17 libdyld.dylib            0x00007fff2048ff3d start + 1
18 libdyld.dylib            0x0000000000000030 start + 18446603339974508788

