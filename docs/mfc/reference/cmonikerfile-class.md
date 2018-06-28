---
title: Třída CMonikerFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
dev_langs:
- C++
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cd166cac7d6d2cddbc12b3cbaa14b28d00c1357
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037266"
---
# <a name="cmonikerfile-class"></a>CMonikerFile – třída
Představuje datový proud ( [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034)) s názvem podle [imoniker –](http://msdn.microsoft.com/library/windows/desktop/ms679705).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Vytvoří `CMonikerFile` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|Umožňuje odpojit a uvolní datového proudu a přezdívka.|  
|[CMonikerFile::Detach](#detach)|Umožňuje odpojit `IMoniker` z tohoto `CMonikerFile` objektu.|  
|[CMonikerFile::GetMoniker](#getmoniker)|Vrátí aktuální přezdívka.|  
|[CMonikerFile::Open](#open)|Otevře se soubor určený k získání datového proudu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|Získá kontext vazby nebo vytvoří výchozí inicializovat kontext vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Přezdívka obsahuje informace, podobně jako cesta k souboru. Pokud máte ukazatel na objekt Přezdívka `IMoniker` rozhraní, můžete získat přístup k identifikovaného souboru bez nutnosti dalších konkrétní informace o tom, kde je soubor nachází ve skutečnosti.  
  
 Odvozené z `COleStreamFile`, `CMonikerFile` trvá přezdívka nebo řetězcová reprezentace mohl zajistit do přezdívka a sváže datového proudu, pro kterou je přezdívka název. Pak můžete číst a zapisovat do tohoto datového proudu. Skutečnému účelu `CMonikerFile` je jednoduchý přístup k poskytnutí `IStream`s s názvem podle `IMoniker`s tak, že nemáte k vytvoření vazby na datový proud sami, ještě `CFile` funkce do datového proudu.  
  
 `CMonikerFile` nelze použít k vytvoření vazby na jakoukoli jinou hodnotu než datového proudu. Pokud chcete vytvořit vazbu úložiště nebo objekt, je nutné použít `IMoniker` rozhraní přímo.  
  
 Další informace o datových proudů a zástupných názvů najdete v tématu [COleStreamFile](../../mfc/reference/colestreamfile-class.md) v *odkaz knihovny MFC* a [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) a [imoniker –](http://msdn.microsoft.com/library/windows/desktop/ms679705) v Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="close"></a>  CMonikerFile::Close  
 Volání této funkce odpojit a verze datového proudu a vydání přezdívka.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Je možné volat na datové proudy vyberte nebo již uzavřen.  
  
##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile  
 Vytvoří `CMonikerFile` objektu.  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext  
 Volání této funkce můžete vytvořit výchozí inicializovat kontext vazby.  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>Parametry  
 *pError*  
 Ukazatel na výjimky souborů. V případě chyby nastaví se na příčinu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na kontext vazby [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) má být svázána s li úspěšné, jinak hodnota **NULL**. Pokud instance byla otevřena s `IBindHost` rozhraní, kontext vazby získává z `IBindHost`. Pokud není žádná `IBindHost` rozhraní nebo rozhraní nepodaří vrátí kontext vazby, vytváření kontextu vazby. Popis [IBindHost](http://msdn.microsoft.com/library/ie/ms775076) rozhraní, najdete v části Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Kontext vazby je objekt, který obsahuje informace o operaci vazbu na konkrétní přezdívka. Tato funkce vám umožňuje kontext vlastní vazby můžete přepsat.  
  
##  <a name="detach"></a>  CMonikerFile::Detach  
 Volání této funkce můžete zavřít datový proud.  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pError*  
 Ukazatel na výjimky souborů. V případě chyby nastaví se na příčinu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker  
 Volání této funkce načíst ukazatel na aktuální přezdívka.  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní aktuální Přezdívka ( [imoniker –](http://msdn.microsoft.com/library/windows/desktop/ms679705)).  
  
### <a name="remarks"></a>Poznámky  
 Vzhledem k tomu `CMonikerFile` není rozhraní, vrácený ukazatel nezvyšuje počet odkazů (prostřednictvím [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379)), a vydání Přezdívka při `CMonikerFile` uvolnění objektu. Pokud chcete k uložení do přezdívka nebo verzi sami, je nutné `AddRef` ho.  
  
##  <a name="open"></a>  CMonikerFile::Open  
 Volání této funkce člena pro otevření objektu souboru nebo přezdívka.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszURL*  
 Adresa URL nebo název souboru, který chcete otevřít.  
  
 *pError*  
 Ukazatel na výjimky souborů. V případě chyby nastaví se na příčinu.  
  
 *pMoniker*  
 Ukazatel rozhraní Přezdívka `IMoniker` k dát použít k získání datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 *LpszURL* parametr nelze použít v počítačích Macintosh. Pouze *pMoniker* formu **otevřete** lze použít v počítačích Macintosh.  
  
 Můžete použít adresu URL nebo název souboru pro *lpszURL* parametr. Příklad:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - nebo –  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [COleStreamFile – třída](../../mfc/reference/colestreamfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
