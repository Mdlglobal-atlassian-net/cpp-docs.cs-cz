---
title: HSE_VERSION_INFO – struktura
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 97f34bebae8a486a825d04b23c5a92fbd4aefa42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322107"
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

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
