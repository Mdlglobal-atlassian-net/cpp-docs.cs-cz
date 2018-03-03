---
title: "CGopherFile – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce90eb2baf4ce8f6ba0136a9efd503086b686aa6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cgopherfile-class"></a>CGopherFile – třída
Poskytuje funkce pro vyhledání a přečtení souborů na gopher serveru.  
  
> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členové jsou zastaralé protože nepracují na platformě Windows XP, ale budou i nadále fungovat na starší operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|Vytvoří `CGopherFile` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Službu gopher neumožňuje uživatelům zapsat data do souboru gopher, protože tato služba funguje především jako nabídkou řízený rozhraní pro vyhledávání informací. `CGopherFile` Členské funkce **zápisu**, `WriteString`, a `Flush` nejsou implementované pro `CGopherFile`. Volání na tyto funkce `CGopherFile` objektu, vrátí [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Další informace o tom, `CGopherFile` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cgopherfile"></a>CGopherFile::CGopherFile  
 Tato funkce člen je volána k sestavení `CGopherFile` objektu.  
  
```  
CGopherFile(
    HINTERNET hFile,  
    CGopherLocator& refLocator,  
    CGopherConnection* pConnection);

 
CGopherFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrLocator,  
    DWORD dwLocLen,  
    DWORD_PTR dwContext);
```  
  
### <a name="parameters"></a>Parametry  
 `hFile`  
 Popisovač pro `HINTERNET` souboru.  
  
 `refLocator`  
 Odkaz na [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu.  
  
 `pConnection`  
 Ukazatel [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objektu.  
  
 `hSession`  
 Popisovač pro aktuální relaci Internet.  
  
 `pstrLocator`  
 Ukazatel na řetězec používaná k nalezení gopher serveru. V tématu [Gopher relací](cgopherlocator-class.md) Další informace o gopher lokátory.  
  
 *dwLocLen*  
 DWORD, který obsahuje počet bajtů v `pstrLocator`.  
  
 `dwContext`  
 Ukazatel na identifikátor kontextu otevíraný soubor.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné `CGopherFile` objektu určeného ke čtení ze souboru během relace gopher Internetu.  
  
 Nikdy vytvoříte `CGopherFile` objektu přímo. Místo toho volat [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) otevřít soubor na serveru gopher.  
  
## <a name="see-also"></a>Viz také  
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection – třída](../../mfc/reference/cgopherconnection-class.md)
