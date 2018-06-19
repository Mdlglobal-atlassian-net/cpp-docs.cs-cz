---
title: Třída CGopherLocator | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 377708108f96a42d23dcf3aa5e8214d7bf9ffe5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366919"
---
# <a name="cgopherlocator-class"></a>CGopherLocator – třída
Získá gopher "Lokátor" ze serveru gopher, určuje typ lokátoru a zpřístupní Lokátor [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).  
  
> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členové jsou zastaralé protože nepracují na platformě Windows XP, ale budou i nadále fungovat na starší operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Vytvoří `CGopherLocator` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyzuje lokátoru gopher a určuje jeho atributy.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Přímý přístup k znaky, které jsou uložené v `CGopherLocator` objekt jako řetězec stylu jazyka C.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikace, musíte si gopher server Lokátor předtím, než bylo možné získat informace z tohoto serveru. Jakmile má Lokátor, ho Lokátor považovat neprůhledného token.  
  
 Každý gopher Lokátor má atributy, které určuje typ souboru nebo na serveru nalezen. V tématu [GetLocatorType](#getlocatortype) seznam typy lokátorů gopher.  
  
 Lokátor aplikace obvykle používá pro volání [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) načíst konkrétní informace.  
  
 Další informace o tom, `CGopherLocator` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator  
 Tato funkce člen je volána k vytvoření `CGopherLocator` objektu.  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>Parametry  
 `ref`  
 Odkaz na konstantu `CGopherLocator` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CGopherLocator` objektu přímo. Místo toho volat [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) vytvořte a vraťte ukazatel `CGopherLocator` objektu.  
  
##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType  
 Volání této funkce člen získat typ lokátoru.  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwRef*  
 Odkaz na `DWORD` , obdrží Typ lokátoru. V tématu **poznámky** pro tabulku Lokátor typů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Možné typy jsou následující:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|Textového souboru ASCII.|  
|GOPHER_TYPE_DIRECTORY|Adresář další Gopher položky.|  
|GOPHER_TYPE_CSO|Server CSO telefonního seznamu.|  
|GOPHER_TYPE_ERROR|Označuje chybový stav.|  
|GOPHER_TYPE_MAC_BINHEX|Macintosh soubor ve formátu BINHEX.|  
|GOPHER_TYPE_DOS_ARCHIVE|Soubor archivu DOS.|  
|GOPHER_TYPE_UNIX_UUENCODED|Soubor UUENCODED.|  
|GOPHER_TYPE_INDEX_SERVER|Server indexu.|  
|GOPHER_TYPE_TELNET|Telnet Server.|  
|GOPHER_TYPE_BINARY|Binární soubor.|  
|GOPHER_TYPE_REDUNDANT|Duplicitní server. Informace obsažené v rámci je duplicitní primární server. Primární server je poslední položky adresáře, který neměl GOPHER_TYPE_REDUNDANT typu.|  
|GOPHER_TYPE_TN3270|TN3270 server.|  
|GOPHER_TYPE_GIF|Grafika soubor GIF.|  
|GOPHER_TYPE_IMAGE|Soubor obrázku.|  
|GOPHER_TYPE_BITMAP|Soubor rastrového obrázku.|  
|GOPHER_TYPE_MOVIE|Soubor filmu.|  
|GOPHER_TYPE_SOUND|Zvukový soubor.|  
|GOPHER_TYPE_HTML|Dokument HTML.|  
|GOPHER_TYPE_PDF|Soubor PDF.|  
|GOPHER_TYPE_CALENDAR|Soubor kalendáře.|  
|GOPHER_TYPE_INLINE|Vloženého souboru.|  
|GOPHER_TYPE_UNKNOWN|Typ položky neznámý.|  
|GOPHER_TYPE_ASK|Požádejte + položku.|  
|GOPHER_TYPE_GOPHER_PLUS|Gopher + položku.|  
  
##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR  
 Tento operátor přetypování užitečné poskytuje efektivní metodu pro přístup k součástí C řetězce ukončené hodnotou null `CGopherLocator` objektu.  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Znak ukazatel na data řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Žádné znaky jsou zkopírovány; Vrátí se pouze ukazatel.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)
