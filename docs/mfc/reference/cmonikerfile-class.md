---
title: CMonikerFile – třída
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504571"
---
# <a name="cmonikerfile-class"></a>CMonikerFile – třída

Představuje datový proud dat ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) s názvem [IMoniker –](/windows/win32/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Syntaxe

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|`CMonikerFile` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMonikerFile:: Close](#close)|Odpojí a uvolní datový proud a uvolní moniker.|
|[CMonikerFile::Detach](#detach)|Odpojí `CMonikerFile` od tohoto objektu. `IMoniker`|
|[CMonikerFile::GetMoniker](#getmoniker)|Vrátí aktuální moniker.|
|[CMonikerFile:: Open](#open)|Otevře zadaný soubor, který získá datový proud.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Získá kontext vazby nebo vytvoří výchozí inicializovaný kontext vazby.|

## <a name="remarks"></a>Poznámky

Moniker obsahuje informace podobně jako cesta k souboru. Máte-li ukazatel na `IMoniker` rozhraní objektu monikeru, můžete získat přístup k identifikovanému souboru bez jakýchkoli jiných konkrétních informací o tom, kde je soubor skutečně umístěn.

Odvozen z `COleStreamFile`, `CMonikerFile` přebírá moniker nebo řetězcové vyjádření, může vytvořit do monikeru a vytvořit vazby ke streamu, pro který je moniker název. Pak můžete tento datový proud číst a zapisovat do něj. Skutečným účelem `CMonikerFile` je poskytnutí jednoduchého přístupu k `IStream`s názvem pomocí `IMoniker`s, takže nemusíte vytvářet vazby ke streamu sami, ale mají `CFile` k němu funkcionalitu.

`CMonikerFile`nejde použít k vytvoření vazby na cokoli jiného než datový proud. Pokud chcete vytvořit `IMoniker` připojení k úložišti nebo objektu, je nutné použít rozhraní přímo.

Další informace o datových proudech a monikerech naleznete v tématu [COleStreamFile](../../mfc/reference/colestreamfile-class.md) in *MFC Reference* and [IStream](/windows/win32/api/objidl/nn-objidl-istream) and [IMoniker –](/windows/win32/api/objidl/nn-objidl-imoniker) in the Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="close"></a>CMonikerFile:: Close

Voláním této funkce odpojíte a uvolníte datový proud a uvolníte moniker.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Lze ji volat v neotevřeném nebo již uzavřeném datovém proudu.

##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

`CMonikerFile` Vytvoří objekt.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext

Voláním této funkce vytvoříte výchozí inicializovaný kontext vazby.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na kontext vazby [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) , se kterým se v případě úspěchu připojí; jinak NULL. Pokud byla instance otevřena s `IBindHost` rozhraním, je kontext vazby načten `IBindHost`z. Pokud není žádné `IBindHost` rozhraní nebo rozhraní nevrátí kontext vazby, vytvoří se kontext vazby. Popis rozhraní [IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) naleznete v Windows SDK.

### <a name="remarks"></a>Poznámky

Kontext vazby je objekt, který ukládá informace o konkrétní operaci vazby monikeru. Tuto funkci můžete přepsat tak, aby poskytovala vlastní kontext vazby.

##  <a name="detach"></a>CMonikerFile::D etach

Voláním této funkce uzavřete datový proud.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="getmoniker"></a>CMonikerFile:: GetMoniker

Voláním této funkce načtete ukazatel na aktuální moniker.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální moniker rozhraní ( [IMoniker –](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Poznámky

Vzhledem `CMonikerFile` k tomu, že není rozhraní, ukazatel, který vrátil, nezvyšuje počet odkazů (prostřednictvím [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)) a moniker `CMonikerFile` je uvolněn při uvolnění objektu. Pokud chcete podržet zástupný název nebo ho vydávat sami, musíte `AddRef` mít.

##  <a name="open"></a>CMonikerFile:: Open

Zavolejte tuto členskou funkci pro otevření souboru nebo objektu monikeru.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Adresa URL nebo název souboru, který se má otevřít

*pError*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

*pMoniker*<br/>
Ukazatel na rozhraní `IMoniker` monikeru, který se má použít k získání datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Parametr *lpszURL* nelze použít v systému Macintosh. V systému Macintosh `Open` lze použít pouze pMoniker formu.

Pro parametr *lpszURL* můžete použít adresu URL nebo název souboru. Příklad:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- nebo –

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Viz také:

[COleStreamFile – třída](../../mfc/reference/colestreamfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
