---
title: CDaoParameterInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368971"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo – struktura

Struktura `CDaoParameterInfo` obsahuje informace o parametru objektu definovaném pro objekty přístupu k datům (DAO). DAO 3.6 je konečná verze, a to je považováno za zastaralé.

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
Jedinečně pojmenuje objekt parametru. Další informace naleznete v tématu "Name Property" v nápovědě dao.

*m_nType*<br/>
Hodnota, která označuje datový typ objektu parametru. Seznam možných hodnot naleznete v *m_nType* člen struktury [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Další informace naleznete v tématu "Type Property" v nápovědě dao.

*m_varValue*<br/>
Hodnota parametru uložená v [cOleVariant](../../mfc/reference/colevariant-class.md) objektu.

## <a name="remarks"></a>Poznámky

Odkazy na primární a sekundární výše označují, jak jsou informace vráceny `CDaoQueryDef`členskou funkcí [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) ve třídě .

Knihovna MFC nezapouzdřuje objekty parametrů DAO ve třídě. DAO querydef objekty `CDaoQueryDef` základní objekty knihovny MFC ukládat parametry v jejich parametry kolekce. Chcete-li získat přístup k objektům parametrů v objektu [CDaoQueryDef,](../../mfc/reference/cdaoquerydef-class.md) zavolejte člennou `GetParameterInfo` funkci objektu querydef pro konkrétní název parametru nebo index do kolekce Parameters. Můžete použít [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) členská funkce `GetParameterInfo` ve spojení s prosmyčce parameters kolekce.

Informace načtené členovou funkcí [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) `CDaoParameterInfo` jsou uloženy ve struktuře. Volání `GetParameterInfo` querydef objektu, v jehož Parametrs kolekce parametr objekt uložených.

> [!NOTE]
> Pokud chcete získat nebo nastavit pouze hodnotu parametru, použijte členské funkce [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) a [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) třídy `CDaoRecordset`.

`CDaoParameterInfo`také definuje `Dump` členská funkce v sestavení ladění. Můžete použít `Dump` k výpisu `CDaoParameterInfo` obsahu objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)
