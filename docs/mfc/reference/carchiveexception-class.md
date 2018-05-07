---
title: Třída CArchiveException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac864831e9d3a0cf0cd5e67501f1ac8396f99473
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="carchiveexception-class"></a>CArchiveException – třída
Představuje podmínku výjimka serializace  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|Vytvoří `CArchiveException` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|Určuje výjimky příčina.|  
|[CArchiveException::m_strFileName](#m_strfilename)|Určuje název souboru pro tuto podmínku výjimky.|  
  
## <a name="remarks"></a>Poznámky  
 `CArchiveException` Třída zahrnuje veřejná data člena, který označuje příčinou výjimky.  
  
 `CArchiveException` objekty jsou vytvořená a vyvolána uvnitř [CArchive](../../mfc/reference/carchive-class.md) členské funkce. Dostanete tyto objekty v rámci oboru **CATCH** výraz. Kód důvodu je nezávislé operačního systému. Další informace o zpracování výjimek najdete v tématu [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException  
 Vytvoří `CArchiveException` objekt, ukládání hodnotu `cause` v objektu.  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cause`  
 Proměnná výčtového typu, která označuje důvod výjimky. Seznam výčty najdete v tématu [m_cause](#m_cause) – datový člen.  
  
 `lpszArchiveName`  
 Odkazuje na řetězec obsahující název `CArchive` objekt, který způsobil výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CArchiveException` objektu v haldě a throw sami nebo nechte globální funkce [afxthrowarchiveexception –](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) zpracování za vás.  
  
 Nepoužívejte tento konstruktor přímo. Místo toho zavolejte globální funkci `AfxThrowArchiveException`.  
  
##  <a name="m_cause"></a>  CArchiveException::m_cause  
 Určuje příčinou výjimky.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen dat je veřejné proměnné typu `int`. Jeho hodnoty jsou definovány `CArchiveException` výčtového typu. Výčty a jejich významy jsou následující:  
  
- **CArchiveException::none** žádné došlo k chybě.  
  
- **CArchiveException::genericException** neurčené chybě.  
  
- **CArchiveException::readOnly** pokusu o zápis v rámci archivu otevřeného pro načtení.  
  
- **CArchiveException::endOfFile** Reached konec souboru při čtení objektu.  
  
- **CArchiveException::writeOnly** pokusu o čtení ze rámci archivu otevřeného pro ukládání.  
  
- **CArchiveException::badIndex** neplatný formát souboru.  
  
- **CArchiveException::badClass** pokusu o čtení objektu na objekt nesprávného typu.  
  
- **CArchiveException::badSchema** pokusu o čtení objektu s jinou verzí třídy.  
  
    > [!NOTE]
    >  Tyto `CArchiveException` výčty příčina se liší od `CFileException` způsobit výčty.  
  
    > [!NOTE]
    > **CArchiveException::generic** je zastaralý. Použití **genericException** místo. Pokud **Obecné** se použijí v aplikaci a vytvořené s volbou/CLR, bude chyby syntaxe, které nejsou snadno dekódovat.  
  
##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName  
 Určuje název souboru pro tuto podmínku výjimky.  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CArchive – třída](../../mfc/reference/carchive-class.md)   
 [Afxthrowarchiveexception –](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [Zpracování výjimek](../../mfc/reference/exception-processing.md)

