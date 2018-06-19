---
title: Třída COleStreamFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
dev_langs:
- C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 805c32145d844cc1103cab7c4987c0595ff5935f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371387"
---
# <a name="colestreamfile-class"></a>COleStreamFile – třída
Představuje datový proud ( `IStream`) v souboru složené jako součást OLE strukturovaných úložiště.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|Vytvoří `COleStreamFile` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|Přidruží objekt datového proudu.|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Vytvoří datový proud z globální paměti a přidruží ji s daným objektem.|  
|[COleStreamFile::CreateStream](#createstream)|Vytvoří datový proud a přidruží ji s daným objektem.|  
|[COleStreamFile::Detach](#detach)|Zrušíte datový proud z objektu.|  
|[COleStreamFile::GetStream](#getstream)|Vrátí aktuální datového proudu.|  
|[COleStreamFile::OpenStream](#openstream)|Bezpečně otevře datového proudu a přidruží ji objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `IStorage` Objektu, musí existovat datového proudu se dá otevřít nebo vytvořit, pokud je datový proud paměti.  
  
 `COleStreamFile` objekty jsou s nimi manipulovat, stejně jako [cfile –](../../mfc/reference/cfile-class.md) objekty.  
  
 Další informace o práci s proudů a úložišť, najdete v článku [kontejnery: složené soubory](../../mfc/containers-compound-files.md)...  
  
 Další informace najdete v tématu [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) a [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="attach"></a>  COleStreamFile::Attach  
 Přidruží zadané OLE datového proudu s `COleStreamFile` objektu.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStream`  
 Odkazuje na datový proud OLE ( `IStream`) být přidruženy k objektu. Nemůže být **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Objekt nesmí být již přidružen OLE datového proudu.  
  
 Další informace najdete v tématu [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) ve Windows SDK.  
  
##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile  
 Vytvoří `COleStreamFile` objektu.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStream`  
 Ukazatel na datový proud OLE být přidruženy k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `lpStream` je **NULL**objekt není přidružen OLE datového proudu, jinak, tento objekt je přidružený s zadaný datový proud OLE.  
  
 Další informace najdete v tématu [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) ve Windows SDK.  
  
##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream  
 Bezpečně vytvoří nový datový proud nedostatek globální, sdílené paměti kde selhání je normální, očekávané podmínku.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pError`  
 Odkazuje na [CFileException](../../mfc/reference/cfileexception-class.md) objekt nebo **NULL** určující stav dokončení operace vytvoření. Zadejte tento parametr, pokud chcete monitorovat možné výjimky generované pokusu o vytvoření datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud datový proud je vytvořen úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Paměť je přidělena subsystém OLE.  
  
 Další informace najdete v tématu [CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) ve Windows SDK.  
  
##  <a name="createstream"></a>  COleStreamFile::CreateStream  
 Bezpečně vytvoří nový datový proud v objektu zadaný úložiště, kde selhání je normální, očekávané podmínku.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStorage`  
 Odkazuje na objekt OLE úložiště, který obsahuje datový proud, který se má vytvořit. Nemůže být **NULL**.  
  
 `lpszStreamName`  
 Název datového proudu, který se má vytvořit. Nemůže být **NULL**.  
  
 `nOpenFlags`  
 Režim přístupu používat při otevírání datového proudu. Exkluzivní, čtení a zápis a vytvořte režimy se používají ve výchozím nastavení. Úplný seznam dostupných režimů, najdete v části [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Odkazuje na [CFileException](../../mfc/reference/cfileexception-class.md) objekt nebo **NULL**. Zadejte tento parametr, pokud chcete monitorovat možné výjimky generované pokusu o vytvoření datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud datový proud je vytvořen úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výjimky souborů bude vyvolána, pokud se nezdaří open a `pError` není **NULL**.  
  
 Další informace najdete v tématu [IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) ve Windows SDK.  
  
##  <a name="detach"></a>  COleStreamFile::Detach  
 Zrušíte datový proud z objektu bez zavírání datového proudu.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datový proud ( `IStream`), který byl přidružený k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Datový proud musí se napřed zavřít nějakým způsobem program se ukončí.  
  
 Další informace najdete v tématu [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) ve Windows SDK.  
  
##  <a name="getstream"></a>  COleStreamFile::GetStream  
 Volání této funkce se vraťte do aktuální datový proud ukazatel.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní aktuální datového proudu ( [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034)).  
  
##  <a name="openstream"></a>  COleStreamFile::OpenStream  
 Otevře existující datového proudu.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStorage`  
 Odkazuje na objekt OLE úložiště, který obsahuje datového proudu k otevření. Nemůže být **NULL**.  
  
 `lpszStreamName`  
 Název datového proudu k otevření. Nemůže být **NULL**.  
  
 `nOpenFlags`  
 Režim přístupu používat při otevírání datového proudu. Výhradní a režimy, které se používají ve výchozím nastavení pro čtení a zápis. Úplný seznam dostupných režimů najdete v tématu [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Odkazuje na [CFileException](../../mfc/reference/cfileexception-class.md) objekt nebo **NULL**. Zadejte tento parametr, pokud chcete monitorovat možné výjimky generované pokusu o otevření datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je datový proud otevřen úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výjimky souborů bude vyvolána, pokud se nezdaří open a `pError` není **NULL**.  
  
 Další informace najdete v tématu [IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



