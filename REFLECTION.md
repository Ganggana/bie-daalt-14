# Reflection — Lab 14

## 1. Аль assertion хамгийн их үнэ цэнэтэй санагдсан вэ? Яагаад?

Миний хувьд хамгийн их үнэ цэнэтэй assertion нь JSON schema/property шалгалт байсан. Учир нь API зөвхөн 200 status code буцаах нь хангалттай биш. Response body дотор шаардлагатай талбарууд байгаа эсэх, тэдгээрийн бүтэц зөв эсэхийг баталгаажуулах нь илүү чухал. Жишээ нь `/posts/1` endpoint дээр `id`, `userId`, `title`, `body` талбарууд байгаа эсэхийг шалгаснаар client application ашиглах contract эвдрэхээс сэргийлж чадна.

## 2. Negative test жишээгээ дэлгэрэнгүй тайлбарла.

Negative test-д байхгүй post ID буюу `/posts/999999` endpoint рүү GET request илгээсэн. Энэ request нь 404 status code буцаах ёстой. Ингэснээр API байхгүй resource хүсэх үед зөв алдааны хариу өгч байгаа эсэхийг шалгана. Хэрэв API 200 буцаавал client тал буруу мэдээлэл авч, алдааг зөв танихгүй байх эрсдэлтэй. Тиймээс negative test нь зөвхөн амжилттай flow биш, алдааны flow ч contract-ийн нэг хэсэг гэдгийг баталдаг.

## 3. Postman дээр ажиллаж байсан тест Newman дээр fail болсон уу? Яагаад?

Энэ collection-д бүх request нь `{{baseUrl}}` environment variable ашигладаг. Хэрэв Newman дээр environment file өгөхгүй ажиллуулбал request fail болох боломжтой. Иймээс Newman ажиллуулахдаа `-e postman/env.dev.json` эсвэл `-e postman/env.ci.json` гэж environment-ийг заавал өгсөн. Environment зөв заагдсан үед Postman болон Newman дээр ижил үр дүн гарна.

## 4. Token эсвэл secret-ыг хэрхэн зохицуулсан вэ?

Сонгосон JSONPlaceholder API нь authentication шаарддаггүй тул real token эсвэл secret ашиглаагүй. Гэхдээ environment variable-ийн соёлыг хадгалахын тулд `baseUrl`-ийг environment file дотор байрлуулсан. Хэрэв token шаардсан API ашигласан бол real token-ыг repository-д commit хийхгүй, оронд нь placeholder эсвэл GitHub Secrets ашиглах байсан.

## 5. API өөрчлөгдвөл collection-ийн аль хэсэг хамгийн их эвдрэх вэ?

API өөрчлөгдвөл хамгийн түрүүнд response body-ийн structure шалгадаг schema/property assertion эвдрэх магадлалтай. Жишээ нь `title` эсвэл `body` талбарын нэр өөрчлөгдвөл test fail болно. Үүнийг бууруулахын тулд collection дээр reusable variables ашиглах, hardcode URL-оос зайлсхийх, зөвхөн үнэхээр contract-д зайлшгүй шаардлагатай талбаруудыг шалгах хэрэгтэй. Мөн API versioning ашиглавал өөрчлөлтөөс үүсэх эвдрэл багасна.
