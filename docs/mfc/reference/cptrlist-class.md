---
title: CPtrList Class
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: 5b88b0950b3b46f9738bd26080883c00d46f8555
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372436"
---
# <a name="cptrlist-class"></a>CPtrList Class

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

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObList – třída](../../mfc/reference/coblist-class.md)
