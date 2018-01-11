---
title: "Třída CInternetException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
dev_langs: C++
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8caa275af4469d45672125677d960b71212fe3de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetexception-class"></a>CInternetException – třída
Představuje podmínku výjimky související s operace Internetu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInternetException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetException::CInternetException](#cinternetexception)|Vytvoří `CInternetException` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetException::m_dwContext](#m_dwcontext)|Hodnota kontextu přidružené operace, který způsobil výjimku.|  
|[CInternetException::m_dwError](#m_dwerror)|Chyba, která způsobila výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 `CInternetException` Třída obsahuje dva členy veřejná data: jeden obsahuje kód chyby související s tím rozdílem, a druhá obsahuje identifikátor kontextu Internetové aplikace přidružené k chybě.  
  
 Další informace o kontextu identifikátory pro webové aplikace, najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cinternetexception"></a>CInternetException::CInternetException  
 Tento člen funkce je volána, když `CInternetException` je vytvořen objekt.  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>Parametry  
 `dwError`  
 Chyba, která způsobila výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li throw CInternetException, volejte globální funkce MFC [afxthrowinternetexception –](internet-url-parsing-globals.md#afxthrowinternetexception).  
  
##  <a name="m_dwcontext"></a>CInternetException::m_dwContext  
 Hodnota kontextu přidružené k související operace Internetu.  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>Poznámky  
 Identifikátor kontextu je byl původně specifikován v [CInternetSession](../../mfc/reference/cinternetsession-class.md) a předaná MFC k [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- a [CInternetFile](../../mfc/reference/cinternetfile-class.md)-odvozených třídách. Můžete přepsat toto výchozí nastavení a přiřazení některého `dwContext` parametr hodnotu dle vlastního výběru. `dwContext`je přidružen k žádné operace daného objektu. `dwContext`identifikuje vrácené informace o stavu operace [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
##  <a name="m_dwerror"></a>CInternetException::m_dwError  
 Chyba, která způsobila výjimku.  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota chyba může být systém kód chyby v nezdařila nalezen. H nebo chybovou hodnotu z WININET. H.  
  
 Seznam kódů chyb Win32 najdete v tématu [kódy chyb](http://msdn.microsoft.com/library/windows/desktop/ms681381). Seznam Internet specifické chybové zprávy najdete v tématu. Obě témata jsou ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)
