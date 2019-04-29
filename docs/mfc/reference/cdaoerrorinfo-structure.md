---
title: CDaoErrorInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: dd9610fce88c18ac42de81ed712492766ee705de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399842"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo – struktura

`CDaoErrorInfo` Struktura obsahuje informace o chybě objekt definovaný pro datový přístup k objektům (DAO).

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
Číselný kód chyby rozhraní DAO. Naleznete v tématu "Zachytitelné chyb přístupu k datům" v nápovědě k DAO.

*m_strSource*<br/>
Název objektu nebo aplikaci, která původně vytvořil chybu. Určuje výraz řetězce představující objekt, který původně vytvořil chybu; vlastnost Source výraz je obvykle název třídy objektu. Podrobnosti naleznete v tématu "Vlastnost Source" v nápovědě k DAO.

*m_strDescription*<br/>
Popisný řetězec přidružený k chybě. Podrobnosti naleznete v tématu "Popis vlastnosti" v nápovědě k DAO.

*m_strHelpFile*<br/>
Plně kvalifikovanou cestu k souboru nápovědě k systému Microsoft Windows. Podrobnosti naleznete v tématu "HelpContext HelpFile – vlastnosti" v nápovědě k DAO.

*m_lHelpContext*<br/>
ID kontextu pro téma v souboru nápovědy pro Microsoft Windows. Podrobnosti naleznete v tématu "HelpContext HelpFile – vlastnosti" v nápovědě k DAO.

## <a name="remarks"></a>Poznámky

Knihovny MFC nejsou zapouzdření rozhraní DAO chyba objekty ve třídě. Místo toho [cdaoexception –](../../mfc/reference/cdaoexception-class.md) třída poskytuje rozhraní pro přístup k kolekce chyb, které jsou součástí objektem DAO `DBEngine` objekt, objekt, který také obsahuje všechny pracovní prostory. Pokud vyvolá operaci knihovny MFC rozhraní DAO `CDaoException` objektu při zachycení, že vyplní knihovny MFC `CDaoErrorInfo` struktury a ukládá ho do objektu výjimky [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) člen. (Pokud se rozhodnete přímo volat rozhraní DAO, musí volat objekt výjimky [GetErrorInfo –](../../mfc/reference/cdaoexception-class.md#geterrorinfo) členskou funkci sami tak, aby vyplnil `m_pErrorInfo`.)

Další informace o zpracování chyb rozhraní DAO, najdete v článku [výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md). Související informace naleznete v tématu "Chyba objekt" v nápovědě k DAO.

Načte informace [CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) členská funkce je uložen v `CDaoErrorInfo` struktury. Zkontrolujte [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) datový člen z `CDaoException` objekt, který najdete v obslužné rutiny výjimky nebo volání `GetErrorInfo` z `CDaoException` objekt, který explicitně vytvoříte za účelem ověření chyby, které může mít došlo k chybě během přímého volání rozhraní DAO. `CDaoErrorInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoErrorInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
