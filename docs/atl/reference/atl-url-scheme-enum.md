---
title: ATL_URL_SCHEME enumeration
ms.date: 11/04/2016
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
ms.openlocfilehash: a63e58349d4339389870de46d5b961fd96db535f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264180"
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

## <a name="see-also"></a>Viz také:

[Koncepty](../active-template-library-atl-concepts.md)<br/>
[CUrl::SetScheme](curl-class.md#setscheme)<br/>
[CUrl::GetScheme](curl-class.md#getscheme)
