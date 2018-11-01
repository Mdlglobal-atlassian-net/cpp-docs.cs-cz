---
title: HSE_VERSION_INFO – struktura
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 6bdb668be037dfaa07e1121e4b61ea332e430e31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577282"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO – struktura

Tato struktura je na které odkazují *pVer* parametr `CHttpServer::GetExtensionVersion` členskou funkci. Obsahuje číslo verze ISA a textový popis ISA.

## <a name="syntax"></a>Syntaxe

```
typedef struct _HSE_VERSION_INFO {
    DWORD dwExtensionVersion;
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;
```

#### <a name="parameters"></a>Parametry

*dwExtensionVersion*<br/>
Číslo verze ISA.

*lpszExtensionDesc*<br/>
Textový popis ISA. Zástupný text; poskytuje výchozí implementaci Přepsat `CHttpServer::GetExtensionVersion` poskytnout vlastní popis.

## <a name="requirements"></a>Požadavky

**Záhlaví:** httpext.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

