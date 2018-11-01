---
title: CDaoRelationFieldInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: 9a00d1cbaf58729863a85d4e9053c9241e9566ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599404"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo – struktura

`CDaoRelationFieldInfo` Struktura obsahuje informace o poli v relaci definované pro datový přístup k objektům (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Název pole v tabulce primárního vztahu.

*m_strForeignName*<br/>
Název pole v tabulce cizího vztahu.

## <a name="remarks"></a>Poznámky

Objekt vztahu DAO určuje pole v primární tabulce a polí v tabulce cizího, které definují vztah. Odkazy na primární ve výše uvedené definice struktury určit, jak vrácené informace v `m_pFieldInfos` členem [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) získán voláním objektu [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)členské funkce třídy `CDaoDatabase`.

Vztah a vztah pole objekty nejsou reprezentovány třídy knihovny MFC. Místo toho objektem DAO objekty základní objekty třídy knihovny MFC [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obsahovat kolekce objektů vztah názvem kolekce vztahů. Každý objekt vztahu zase obsahuje kolekci objektů pole relace. Každý objekt pole vztah koreluje s poli v tabulce cizího pole v primární tabulce. Společně pole objektů vztah definují skupinu polí v každé tabulce, které společně definují vztah. `CDaoDatabase` Umožňuje vám přístup k objektům vztah s `CDaoRelationInfo` objektu voláním `GetRelationInfo` členskou funkci. `CDaoRelationInfo` Objektu, pak má datový člen, `m_pFieldInfos`, který odkazuje na pole `CDaoRelationFieldInfo` objekty.

Volání [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) členskou funkci nadřazeného `CDaoDatabase` objektu ve jehož relace kolekce je uložený objekt relace vás zajímají. Přejděte k `m_pFieldInfos` člena [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objektu. `CDaoRelationFieldInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoRelationFieldInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoRelationInfo – struktura](../../mfc/reference/cdaorelationinfo-structure.md)
