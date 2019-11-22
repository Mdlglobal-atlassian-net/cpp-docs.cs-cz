---
title: CDaoErrorInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304235"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo – struktura

Struktura `CDaoErrorInfo` obsahuje informace o objektu Error definovaném pro objekty DAO (Data Access Object). Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

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

Knihovna MFC neprovádí zapouzdření objektů chyb DAO ve třídě. Místo toho třída [CDaoException](../../mfc/reference/cdaoexception-class.md) poskytuje rozhraní pro přístup ke kolekci chyb obsažené v objektu DAO `DBEngine` objekt, který obsahuje také všechny pracovní prostory. Když operace knihovny MFC rozhraní DAO vyvolá objekt `CDaoException`, který zachytíte, knihovna MFC vyplní strukturu `CDaoErrorInfo` a uloží ji do [m_pErrorInfoho](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) člena objektu výjimky. (Pokud se rozhodnete volat rozhraní DAO přímo, je nutné zavolat členskou funkci [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) objektu Exception sami sebe k vyplnění `m_pErrorInfo`.)

Další informace o zpracování chyb DAO naleznete v článku [výjimky databáze](../../mfc/exceptions-database-exceptions.md). Související informace naleznete v tématu "chybový objekt" v nápovědě k rozhraní DAO.

Informace načtené členskou funkcí [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) jsou uloženy ve struktuře `CDaoErrorInfo`. Prostudujte datový člen [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) z objektu `CDaoException`, který zachytíte v obslužné rutině výjimky, nebo zavolejte `GetErrorInfo` z objektu `CDaoException`, který vytvoříte explicitně, aby bylo možné kontrolovat chyby, k nimž mohlo dojít během přímého volání rozhraní DAO. `CDaoErrorInfo` také definuje členskou funkci `Dump` v sestaveních ladění. K výpisu obsahu `CDaoErrorInfo` objektu můžete použít `Dump`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
