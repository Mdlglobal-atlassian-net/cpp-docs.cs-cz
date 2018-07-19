---
title: Colestreamfile – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 9304c4e3dfd559b296c69b274c1462f2f973a04d
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852755"
---
# <a name="colestreamfile-class"></a>Colestreamfile – třída
Představuje datový proud (`IStream`) ve složeném souboru jako součást strukturovaného úložiště OLE.  
  
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
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Vytvoří datový proud z globální paměti a přidruží ji k objektu.|  
|[COleStreamFile::CreateStream](#createstream)|Vytvoří datový proud a přidruží ji k objektu.|  
|[COleStreamFile::Detach](#detach)|Zruší přidružení datový proud z objektu.|  
|[COleStreamFile::GetStream](#getstream)|Vrátí aktuální datový proud.|  
|[COleStreamFile::OpenStream](#openstream)|Bezpečně se otevře datový proud a přidruží ji k objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `IStorage` Objektu musí existovat předtím, než se dá otevřít nebo vytvořit, pokud je datový proud paměti datového proudu.  
  
 `COleStreamFile` objekty jsou manipulovat stejným způsobem jako [cfile –](../../mfc/reference/cfile-class.md) objekty.  
  
 Další informace o zpracování datových proudů a úložišť, najdete v článku [kontejnery: složené soubory](../../mfc/containers-compound-files.md)...  
  
 Další informace najdete v tématu [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) a [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) v sadě Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="attach"></a>  COleStreamFile::Attach  
 Přidruží zadaný stream OLE se `COleStreamFile` objektu.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStream*  
 Odkazuje na datový proud OLE (`IStream`) má být přidružena k objektu. Nemůže mít hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Objekt nesmí být již přidružen proud OLE.  
  
 Další informace najdete v tématu [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) v sadě Windows SDK.  
  
##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile  
 Vytvoří `COleStreamFile` objektu.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStream*  
 Ukazatel na datový proud OLE má být přidružena k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *lpStream* má hodnotu NULL, není objekt přidružen proud OLE, v opačném případě objekt je přidružený zadaný stream OLE.  
  
 Další informace najdete v tématu [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) v sadě Windows SDK.  
  
##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream  
 Bezpečně vytvoří nový datový proud z globální sdílenou paměť kde selhání je normální, očekávaný stav.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pError*  
 Odkazuje [cfileexception –](../../mfc/reference/cfileexception-class.md) objekt nebo hodnota NULL, která označuje stav dokončení operace vytvoření. Tento parametr zadejte, pokud chcete sledovat výjimky generované pokusu o vytvoření datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud datový proud je vytvořen úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Paměť je přidělena subsystému OLE.  
  
 Další informace najdete v tématu [CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) v sadě Windows SDK.  
  
##  <a name="createstream"></a>  COleStreamFile::CreateStream  
 Bezpečně vytvoří nový datový proud v objekt zadaný úložiště, kde je normální, očekávaný stav selhání.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStorage*  
 Odkazuje na objekt OLE úložiště, který obsahuje datový proud, který se má vytvořit. Nemůže mít hodnotu NULL.  
  
 *lpszStreamName*  
 Název datového proudu, který se má vytvořit. Nemůže mít hodnotu NULL.  
  
 *nOpenFlags*  
 Režim přístupu k použití při otevření datového proudu. Exkluzivní, čtení a zápisu a vytvořit režimy se používají ve výchozím nastavení. Úplný seznam dostupných režimů, naleznete v tématu [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 *pError*  
 Odkazuje [cfileexception –](../../mfc/reference/cfileexception-class.md) objekt nebo hodnotu NULL. Tento parametr zadejte, pokud chcete sledovat výjimky generované pokusu o vytvoření datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud datový proud je vytvořen úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud selže otevřít, bude vyvolána výjimka souboru a *pError* nemá hodnotu NULL.  
  
 Další informace najdete v tématu [IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) v sadě Windows SDK.  
  
##  <a name="detach"></a>  COleStreamFile::Detach  
 Zruší přidružení datový proud z objektu bez zavření datového proudu.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datový proud (`IStream`), který je přidružený k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Datový proud musí být uzavřen nějak jiných než program se ukončí.  
  
 Další informace najdete v tématu [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) v sadě Windows SDK.  
  
##  <a name="getstream"></a>  COleStreamFile::GetStream  
 Voláním této funkce vrací ukazatel na aktuální datový proud.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální datový proud rozhraní ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)).  
  
##  <a name="openstream"></a>  COleStreamFile::OpenStream  
 Otevře existující datový proud.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStorage*  
 Odkazuje na objekt OLE úložiště, který obsahuje datového proudu k otevření. Nemůže mít hodnotu NULL.  
  
 *lpszStreamName*  
 Název datového proudu k otevření. Nemůže mít hodnotu NULL.  
  
 *nOpenFlags*  
 Režim přístupu k použití při otevření datového proudu. Výhradní a čtení/zápis režimy se používají ve výchozím nastavení. Úplný seznam dostupných režimů najdete v tématu [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 *pError*  
 Odkazuje [cfileexception –](../../mfc/reference/cfileexception-class.md) objekt nebo hodnotu NULL. Tento parametr zadejte, pokud chcete sledovat výjimky generované při pokusu o otevření datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud datový proud je otevřen úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud selže otevřít, bude vyvolána výjimka souboru a *pError* nemá hodnotu NULL.  
  
 Další informace najdete v tématu [IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



