---
title: CDaoParameterInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 29248f04833662750d99b112fe2386c6ff4d97fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545909"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo – struktura

`CDaoParameterInfo` Struktura obsahuje informace o parametru objekt definovaný pro datový přístup k objektům (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Jedinečné názvy parametrem objektu. Další informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_nType*<br/>
Hodnota, která určuje datový typ parametru objektu. Seznam možných hodnot najdete v tématu *m_nType* člena [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Další informace naleznete v tématu "Vlastnost typu" v nápovědě k DAO.

*m_varValue*<br/>
Hodnota parametru uložené v [COleVariant](../../mfc/reference/colevariant-class.md) objektu.

## <a name="remarks"></a>Poznámky

Odkazy na primární a sekundární výše určit, jak vrácené informace [getparameterinfo –](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) členské funkce ve třídě `CDaoQueryDef`.

Knihovny MFC nejsou zapouzdření rozhraní DAO parametr objekty ve třídě. Objekty základní knihovny MFC rozhraní DAO querydef `CDaoQueryDef` objekty uložit parametry do kolekce jejich parametry. Pro přístup k objektům parametr v [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md) objektu, volání objektu querydef `GetParameterInfo` členskou funkci pro konkrétní název parametru nebo indexu v kolekci parametrů. Můžete použít [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) členské funkce ve spojení s `GetParameterInfo` k vytvoření smyčky přes kolekce parametrů.

Načte informace [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) členská funkce je uložen v `CDaoParameterInfo` struktury. Volání `GetParameterInfo` querydef objektu, v jehož kolekce parametrů je objekt parametr uložen.

> [!NOTE]
>  Pokud chcete získat nebo nastavit pouze hodnoty parametru, použijte [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) a [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) členské funkce třídy `CDaoRecordset`.

`CDaoParameterInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoParameterInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)
