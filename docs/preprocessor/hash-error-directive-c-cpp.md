---
title: '#error – direktiva (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: bfb5c18f20319e6e6d345f28d3e1850714334b71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216118"
---
# <a name="error-directive-cc"></a>#error direktiva (CC++/)

Direktiva **#error** emituje uživatelem zadanou chybovou zprávu v době kompilace a pak ukončí kompilaci.

## <a name="syntax"></a>Syntaxe

> **#error** *token – řetězec*

## <a name="remarks"></a>Poznámky

Chybová zpráva, kterou tato direktiva generuje, zahrnuje parametr *řetězce tokenu* . Parametr *řetězce tokenu* nepodléhá rozšíření makra. Tato direktiva je nejužitečnější během předběžného zpracování, která upozorní vývojáře na nekonzistenci programu nebo porušení omezení. Následující příklad ukazuje zpracování chyb během předběžného zpracování:

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
