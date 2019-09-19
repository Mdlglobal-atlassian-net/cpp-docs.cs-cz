---
title: CDaoErrorInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: a7b273bd2aa6b428bf795c1842455b8bfe187cc8
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096140"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo – struktura

`CDaoErrorInfo` Struktura obsahuje informace o objektu Error definovaném pro objekty DAO (Data Access Objects).
Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.


## <a name="syntax"></a>Syntaxe

```
struct CDaoErrorInfo
{
    long m_lErrorCode;
    CString m_strSource;
    CString m_strDescription;
    CString m_strHelpFile;
    long m_lHelpContext;
};
```

#### <a name="parameters"></a>Parametry

*m_lErrorCode*<br/>
Číselný kód chyby rozhraní DAO. Informace najdete v nápovědě k rozhraní DAO v tématu "chyby při přístupu k datům k zachytávání".

*m_strSource*<br/>
Název objektu nebo aplikace, které původně vygenerovaly chybu. Vlastnost source Určuje řetězcový výraz představující objekt, který původně vygeneroval chybu. výraz je obvykle název třídy objektu. Podrobnosti najdete v tématu "zdrojová vlastnost" v nápovědě k rozhraní DAO.

*m_strDescription*<br/>
Popisný řetězec přidružený k chybě Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost popisu".

*m_strHelpFile*<br/>
Plně kvalifikovaná cesta k souboru s nápovědě systému Microsoft Windows. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "atribut HelpContext, vlastnosti panelu vlastností".

*m_lHelpContext*<br/>
ID kontextu pro téma v souboru nápovědy systému Microsoft Windows. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "atribut HelpContext, vlastnosti panelu vlastností".

## <a name="remarks"></a>Poznámky

Knihovna MFC neprovádí zapouzdření objektů chyb DAO ve třídě. Místo toho třída [CDaoException](../../mfc/reference/cdaoexception-class.md) poskytuje rozhraní pro přístup ke kolekci chyb obsaženým v objektu DAO `DBEngine` , objekt, který obsahuje také všechny pracovní prostory. Když operace knihovny MFC rozhraní DAO vyvolá `CDaoException` objekt, který zachytíte, knihovna `CDaoErrorInfo` MFC vyplní strukturu a uloží ji do [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) člena objektu výjimky. (Pokud se rozhodnete volat rozhraní DAO přímo, je nutné zavolat členskou funkci [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) objektu Exception sami, abyste mohli `m_pErrorInfo`vyplnit.)

Další informace o zpracování chyb DAO naleznete v článku [výjimky: Výjimky](../../mfc/exceptions-database-exceptions.md)databáze. Související informace naleznete v tématu "chybový objekt" v nápovědě k rozhraní DAO.

Informace načtené členskou funkcí [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) jsou uloženy ve `CDaoErrorInfo` struktuře. Prohlédněte si datový člen [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) z `CDaoException` objektu, který zachytíte v obslužné rutině výjimky `GetErrorInfo` , `CDaoException` nebo zavolejte z objektu, který vytvoříte explicitně, aby se zkontrolovaly chyby, které mohly nastat během přímého volání. rozhraní DAO. `CDaoErrorInfo`také definuje `Dump` členskou funkci v sestavení ladění. Můžete použít `Dump` k výpisu obsahu `CDaoErrorInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
