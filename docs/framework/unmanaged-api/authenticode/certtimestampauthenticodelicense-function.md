---
title: CertTimestampAuthenticodeLicense 함수
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd77a8a81718837d55f3018564d0f4ba8fdc95ee
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508545"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense 함수
Authenticode XrML 라이선스에 타임스탬프를 적용합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pSignedLicenseBlob`  
 [in] 타임스탬프를 적용할 서명된 Authenticode XrML 라이선스입니다. 참조 된 [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) 구조입니다.  
  
 `pwszTimestampURI`  
 [in] 타임스탬프 서버의 URI입니다.  
  
 `pTimestampSignatureBlob`  
 [out] base64로 인코딩된 타임스탬프 서명을 받을 CRYPT_DATA_BLOB에 대한 포인터입니다. 무료 호출자의 책임 `pTimestampSignatureBlob` -> `pbData` 사용 하 여 `HepFree()` 후 사용 합니다. 참조 된 [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) 구조입니다.  
  
## <a name="remarks"></a>설명  
 타임스탬프 서명은 실제로는 해당 콘텐츠가 라이선스 서명에 있는 SignatureValue의 이진 형식인 PKCS #7 SignedData 메시지이며, 기본적으로 라이선스의 연대 서명으로 작동합니다.  
  
## <a name="return-value"></a>반환 값  
 함수가 정상적으로 실행되는 경우 `S_OK`입니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
