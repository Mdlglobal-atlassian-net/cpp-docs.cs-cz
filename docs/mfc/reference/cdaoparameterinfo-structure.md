---
title: CDaoParameterInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 4f0ee7ebe1d5d4eff50194c2d5c5cccf8f373c61
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096081"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo – struktura

`CDaoParameterInfo` Struktura obsahuje informace o objektu parametru definovaném pro objekty DAO (Data Access Objects).
Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.


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
Jedinečně pojmenuje objekt parametru. Další informace najdete v nápovědě k rozhraní DAO v tématu "vlastnost názvu".

*m_nType*<br/>
Hodnota, která určuje datový typ objektu parametru. Seznam možných hodnot naleznete v tématu *m_nType* člen struktury [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) . Další informace naleznete v nápovědě k rozhraní DAO v tématu "vlastnost typu".

*m_varValue*<br/>
Hodnota parametru uložená v objektu [COleVariant](../../mfc/reference/colevariant-class.md) .

## <a name="remarks"></a>Poznámky

Odkazy na primární a sekundární výše označují, jak jsou informace vráceny členskou funkcí [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) ve třídě `CDaoQueryDef`.

Knihovna MFC nepoužívá zapouzdření objektů parametrů DAO ve třídě. Objekty DAO v podkladových objektech knihovny MFC `CDaoQueryDef` ukládají parametry do kolekcí parametrů. Chcete-li získat přístup k objektům parametrů v objektu [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , zavolejte `GetParameterInfo` členskou funkci objektu querydef pro konkrétní název parametru nebo index do kolekce Parameters. Můžete použít členskou funkci [CDaoQueryDef:: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) ve spojení s `GetParameterInfo` smyčkou prostřednictvím kolekce Parameters.

Informace načtené členskou funkcí [CDaoQueryDef:: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) jsou uloženy ve `CDaoParameterInfo` struktuře. Volání `GetParameterInfo` objektu QueryDef, v jehož kolekcích parametrů je objekt Parameter uložen.

> [!NOTE]
>  Pokud chcete získat nebo nastavit pouze hodnotu parametru, použijte členské funkce třídy `CDaoRecordset` [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) a [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) .

`CDaoParameterInfo`také definuje `Dump` členskou funkci v sestavení ladění. Můžete použít `Dump` k výpisu obsahu `CDaoParameterInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)
