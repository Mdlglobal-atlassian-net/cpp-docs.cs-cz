---
title: Cgopherfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6c4f87ffb1538e581320e9d6f36e8d4fbc6fc12
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335679"
---
# <a name="cgopherfile-class"></a>Cgopherfile – třída
Poskytuje funkce pro hledání a čtení souborů na gopher serveru.  
  
> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členy jsou zastaralé, protože nebude fungovat na platformě Windows XP, ale budou i nadále fungovat na starší platformy.  
  
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
 Služba gopher nedovoluje uživatelům k zápisu dat do souboru gopher, protože tato služba functions především jako nabídkou řízený rozhraní pro hledání informací. `CGopherFile` Členské funkce `Write`, `WriteString`, a `Flush` nejsou implementovány pro `CGopherFile`. Volání těchto funkcí na `CGopherFile` objektu, vrátí [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Další informace o tom, `CGopherFile` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [Cstdiofile –](../../mfc/reference/cstdiofile-class.md)  
  
 [Cinternetfile –](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile  
 Tato členská funkce je volána k sestavení kompletních `CGopherFile` objektu.  
  
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
 *hfile –*  
 Popisovač souboru HINTERNET.  
  
 *refLocator*  
 Odkaz na [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu.  
  
 *pConnection*  
 Ukazatel [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md) objektu.  
  
 *hSession*  
 Popisovač s aktuální relací Internetu.  
  
 *pstrLocator*  
 Ukazatel na řetězec používaná k nalezení gopher serveru. Zobrazit [Gopher relace](cgopherlocator-class.md) Další informace o gopher lokátory.  
  
 *dwLocLen*  
 Hodnota DWORD obsahující počet bajtů v *pstrLocator*.  
  
 *dwContext*  
 Ukazatel na identifikátor kontextu právě otevřený soubor.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné `CGopherFile` objektu určeného ke čtení ze souboru během relace gopher Internet.  
  
 Nikdy nevytvářejte `CGopherFile` objektu přímo. Namísto toho zavolejte metodu [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) otevřít soubor na gopher serveru.  
  
## <a name="see-also"></a>Viz také  
 [Cinternetfile – třída](../../mfc/reference/cinternetfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cinternetfile – třída](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherlocator – třída](../../mfc/reference/cgopherlocator-class.md)   
 [Cgopherfilefind – třída](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection – třída](../../mfc/reference/cgopherconnection-class.md)
