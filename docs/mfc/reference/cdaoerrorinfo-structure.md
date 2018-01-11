---
title: "Cdaoerrorinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoErrorInfo
dev_langs: C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da47b4b68a9fd73b3962254121006eff47282336
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo – struktura
`CDaoErrorInfo` Struktura obsahuje informace o chybě objekt definovaný pro přístup k objektům dat (DAO).  
  
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
 *m_lErrorCode*  
 Číselný kód chyby rozhraní DAO. Naleznete v tématu "Zachytitelné chyb přístupu k datům" v nápovědě rozhraní DAO.  
  
 *m_strSource*  
 Název objektu nebo aplikace, který původně vytvořil chybu. Vlastnost Source Určuje výraz řetězce představující objekt, který původně vytvořil chybu; výraz je obvykle název třídy objektu. Podrobnosti naleznete v tématu "Zdrojová vlastnost" v nápovědě rozhraní DAO.  
  
 *m_strDescription*  
 Popisný řetězec přidružený k chybě. Podrobnosti naleznete v tématu "Popis vlastnost" v nápovědě rozhraní DAO.  
  
 *m_strHelpFile*  
 Plně kvalifikovanou cestu k souboru nápovědy pro Microsoft Windows. Podrobnosti naleznete v tématu "HelpContext HelpFile – vlastnosti" v nápovědě rozhraní DAO.  
  
 *m_lHelpContext*  
 ID kontextu pro téma v souboru nápovědy pro Microsoft Windows. Podrobnosti naleznete v tématu "HelpContext HelpFile – vlastnosti" v nápovědě rozhraní DAO.  
  
## <a name="remarks"></a>Poznámky  
 MFC není zapouzdření rozhraní DAO chyba objekty ve třídě. Místo toho [CDaoException](../../mfc/reference/cdaoexception-class.md) třída poskytuje rozhraní pro přístup k kolekce chyb, které jsou součástí s objektem DAO **databázový stroj** objektu, objekt, který také obsahuje všechny pracovní prostory. Když vyvolá operace knihovny MFC rozhraní DAO `CDaoException` objekt, můžete zachytit, vyplní celé MFC `CDaoErrorInfo` struktury a ukládá je objekt výjimky [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) člen. (Pokud zvolíte možnost DAO volat přímo, musí volat objekt výjimky [GetErrorInfo –](../../mfc/reference/cdaoexception-class.md#geterrorinfo) – členská funkce sami k vyplnění `m_pErrorInfo`.)  
  
 Další informace o zpracování chyb DAO, najdete v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md). Související informace naleznete v tématu "Chyba objekt" v nápovědě rozhraní DAO.  
  
 Načte informace [CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) – členská funkce je uložen v `CDaoErrorInfo` struktura. Zkontrolujte [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) – datový člen z `CDaoException` objekt, který catch v obslužná rutina výjimky, nebo volání `GetErrorInfo` z `CDaoException` objekt, který vytvoříte explicitně aby kontrolovat chyby, které by mohly mít došlo k během přímé volání rozhraní DAO. `CDaoErrorInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoErrorInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
