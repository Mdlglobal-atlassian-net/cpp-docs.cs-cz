---
title: '#Chyba – direktiva (C++)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: dc229a8eae6938cba32787ecbec6a5aa6a17ab47
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037841"
---
# <a name="error-directive-cc"></a>#error – direktiva (C++)
**#Error** – direktiva generuje zadané uživatelem chybovou zprávu v době kompilace a ukončí kompilace.

## <a name="syntax"></a>Syntaxe

```
#errortoken-string
```

## <a name="remarks"></a>Poznámky

Obsahuje chybovou zprávu, která tato direktiva generuje *řetězci tokenu* parametru. *Řetězci tokenu* parametr není řídí podle rozšíření makra. Tato direktiva je nejužitečnější při předběžném zpracování oznamujících developer program nekonzistence nebo porušení omezení. Následující příklad ukazuje Chyba při zpracování během předběžného zpracování:

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Viz také:

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)