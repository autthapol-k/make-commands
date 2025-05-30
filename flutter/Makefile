build-gen:
	dart run build_runner build --delete-conflicting-outputs

build-watch:
	dart run build_runner watch --delete-conflicting-outputs

build-slang:
	dart run slang

pub-get:
	flutter pub get

clean:
	flutter clean

format:
	dart format . --line-length $(or $(length),100)

fix:
	dart fix --apply --code $(rule)

flavor-gen:
	flutter pub run flutter_flavorizr -p assets:download,assets:extract,android:androidManifest,android:buildGradle,android:dummyAssets,android:icons,ios:podfile,ios:xcconfig,ios:buildTargets,ios:schema,ios:dummyAssets,ios:icons,ios:plist,google:firebase,huawei:agconnect,assets:clean,ide:config

test-coverage:
	flutter test --coverage
	lcov --extract coverage/lcov.info '**/bloc/**' '**/use_cases/**' '**/repositories/**' -o coverage/lcov.info
	genhtml coverage/lcov.info -o coverage/html
	open coverage/html/index.html