---
title: Výčet ATL_URL_SCHEME | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee13d34bcea1e7ce2e53b0659739ee730152f287
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755408"
---
# <a name="atlurlscheme"></a>ATL_URL_SCHEME  

Členů tohoto výčtu poskytují konstanty pro režimy rozumí [CUrl](curl-class.md).

## <a name="syntax"></a>Syntaxe

```

      enum ATL_URL_SCHEME{  
   ATL_URL_SCHEME_UNKNOWN = -1,  
   ATL_URL_SCHEME_FTP     = 0,  
   ATL_URL_SCHEME_GOPHER  = 1,  
   ATL_URL_SCHEME_HTTP    = 2,  
   ATL_URL_SCHEME_HTTPS   = 3,  
   ATL_URL_SCHEME_FILE    = 4,  
   ATL_URL_SCHEME_NEWS    = 5,  
   ATL_URL_SCHEME_MAILTO  = 6,  
   ATL_URL_SCHEME_SOCKS   = 7  
};  
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="see-also"></a>Viz také

[Koncepty](../active-template-library-atl-concepts.md)   
[CUrl::SetScheme](curl-class.md#setscheme)   
[CUrl::GetScheme](curl-class.md#getscheme)