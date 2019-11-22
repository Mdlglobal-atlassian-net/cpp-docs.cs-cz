---
title: CDaoParameterInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 9f96cba8ea43db7e24e834b1de4ffb593b2c6e0d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303481"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo – struktura

Struktura `CDaoParameterInfo` obsahuje informace o objektu parametru definovaném pro objekty DAO (Data Access Objects). Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

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

Knihovna MFC nepoužívá zapouzdření objektů parametrů DAO ve třídě. Objekty DAO querydef objekty knihovny MFC `CDaoQueryDef` objekty ukládají parametry do kolekcí parametrů. Chcete-li získat přístup k objektům parametrů v objektu [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , zavolejte členskou funkci `GetParameterInfo` objektu querydef pro konkrétní název parametru nebo index do kolekce Parameters. Můžete použít členskou funkci [CDaoQueryDef:: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) ve spojení s `GetParameterInfo` ke smyčce prostřednictvím kolekce Parameters.

Informace načtené členskou funkcí [CDaoQueryDef:: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) jsou uloženy ve struktuře `CDaoParameterInfo`. Zavolejte `GetParameterInfo` pro objekt querydef, v jehož kolekci parametrů je uložený objekt Parameter.

> [!NOTE]
>  Pokud chcete získat nebo nastavit pouze hodnotu parametru, použijte členské funkce [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) a [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) třídy `CDaoRecordset`.

`CDaoParameterInfo` také definuje členskou funkci `Dump` v sestaveních ladění. K výpisu obsahu `CDaoParameterInfo` objektu můžete použít `Dump`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)
