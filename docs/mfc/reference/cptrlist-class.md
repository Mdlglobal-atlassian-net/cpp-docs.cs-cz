---
title: Cptrlist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97eeeaaa2eea237eebda4f945f2c810268f406cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384959"
---
# <a name="cptrlist-class"></a>Cptrlist – třída

Podporuje seznamy ukazatelů void.

## <a name="syntax"></a>Syntaxe

```
class CPtrList : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CPtrList` jsou podobné jako u členských funkcí třídy [coblist –](../../mfc/reference/coblist-class.md). Z důvodu podobnosti, můžete použít `CObList` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení `CObject` ukazatele jako parametr funkce nebo návratová hodnota, nahraďte ukazatel na **void**.

`CObject*& CObList::GetHead() const;`

například se přeloží na

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Poznámky

`CPtrList` zahrnuje IMPLEMENT_DYNAMIC – makro pro podporu přístupu typu modulu runtime a k vypsání `CDumpContext` objektu. Pokud potřebujete s výpisem paměti jednotlivých ukazatel seznam prvků, nastavte na 1 nebo větší hloubky kontextu s výpisem paměti.

Seznamy ukazatel nejde serializovat.

Když `CPtrList` odstranění objektu nebo při jeho prvky jsou odebrány, odeberou se jenom ukazatele, není entity, které odkazují.

Další informace o používání `CPtrList`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObList – třída](../../mfc/reference/coblist-class.md)
