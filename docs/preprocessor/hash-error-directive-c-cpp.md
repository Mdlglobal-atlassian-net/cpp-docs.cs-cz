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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383982"
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