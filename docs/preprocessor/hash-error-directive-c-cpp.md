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
ms.openlocfilehash: c83fc7ef8135ee0cba37a956df47bcab0f796007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447811"
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

## <a name="see-also"></a>Viz také

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)