---
title: Cmonikerfile – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 977bf0a56e21ddbef62daf88a7aa459d7c275a99
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405234"
---
# <a name="cmonikerfile-class"></a>Cmonikerfile – třída

Představuje datový proud ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)) s názvem podle [imoniker –](/windows/desktop/api/objidl/nn-objidl-imoniker).

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
|[CMonikerFile::Close](#close)|Odpojí a uvolní datového proudu a monikeru.|
|[CMonikerFile::Detach](#detach)|Odpojí `IMoniker` z tohoto `CMonikerFile` objektu.|
|[CMonikerFile::GetMoniker](#getmoniker)|Vrátí aktuální moniker.|
|[CMonikerFile::Open](#open)|Otevře se soubor určený k získání datového proudu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Získá kontext vazby nebo vytvoří kontext vazby inicializované ve výchozím nastavení.|

## <a name="remarks"></a>Poznámky

Moniker informacemi, podobně jako cesta k souboru. Pokud máte ukazatel na objekt moniker `IMoniker` rozhraní, můžete získat přístup k zjištěného souboru bez nutnosti žádné konkrétní informace o tom, kde soubor nachází ve skutečnosti.

Odvozené od `COleStreamFile`, `CMonikerFile` monikeru nebo řetězcovou reprezentaci lze vytvořit jako monikeru a váže k datovému proudu, pro kterou je moniker je název. Potom může číst a zapisovat do tohoto datového proudu. Skutečnému účelu `CMonikerFile` je poskytnout jednoduchý přístup k `IStream`s názvem `IMoniker`s tak, že není nutné vytvořit vazbu na datový proud sami, ještě `CFile` funkce do datového proudu.

`CMonikerFile` nelze použít k vytvoření vazby na jinou hodnotu než datového proudu. Pokud chcete vytvořit vazbu na úložiště nebo objekt, je nutné použít `IMoniker` rozhraní přímo.

Další informace o datových proudů a zástupných názvů najdete v tématu [colestreamfile –](../../mfc/reference/colestreamfile-class.md) v *odkaz knihovny MFC* a [IStream](/windows/desktop/api/objidl/nn-objidl-istream) a [imoniker –](/windows/desktop/api/objidl/nn-objidl-imoniker) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cfile –](../../mfc/reference/cfile-class.md)

[Colestreamfile –](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="close"></a>  CMonikerFile::Close

Voláním této funkce pro odpojení a uvolnění datového proudu a uvolnit monikeru.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Můžete volat u neotevřených "nebo" již uzavřeno streamů.

##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile

Vytvoří `CMonikerFile` objektu.

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

Voláním této funkce k vytvoření kontextu vazby inicializované ve výchozím nastavení.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Ukazatel na soubor výjimku. V případě chyby bude nastavena na příčinu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel do kontextu vazby [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) má být svázána s Pokud úspěšné; jinak hodnota NULL. Pokud instance byla otevřena s `IBindHost` rozhraní, kontextu vazby je načten z `IBindHost`. Pokud není žádný `IBindHost` rozhraní nebo rozhraní se nepodařilo vrátit kontext vazby, kontextu vazby je vytvořen. Popis [IBindHost](https://msdn.microsoft.com/library/ie/ms775076) rozhraní, naleznete v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Kontext vazby je objekt, který obsahuje informace o operaci konkrétní zástupný název vazby. Můžete přepsat tuto funkci pro poskytnutí kontextu vlastní vazby.

##  <a name="detach"></a>  CMonikerFile::Detach

Voláním této funkce ukončení datového proudu.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Ukazatel na soubor výjimku. V případě chyby bude nastavena na příčinu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

Volání této funkce načtete ukazatel na aktuální moniker.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální moniker rozhraní ( [imoniker –](/windows/desktop/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Poznámky

Protože `CMonikerFile` není rozhraní, vrácený ukazatel se nezvyšuje počet odkazů (prostřednictvím [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)), a monikeru je uvolněna při `CMonikerFile` uvolnění objektu. Pokud chcete opřete se o monikeru nebo uvolnění sami, je nutné `AddRef` ho.

##  <a name="open"></a>  CMonikerFile::Open

Voláním této členské funkce pro otevření objektu souboru nebo moniker.

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
Adresa URL nebo název souboru, který má být otevřen.

*pError*<br/>
Ukazatel na soubor výjimku. V případě chyby bude nastavena na příčinu.

*pMoniker*<br/>
Ukazatel na rozhraní moniker `IMoniker` se použije k získání datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

*LpszURL* parametr nelze použít v počítačích Macintosh. Pouze *pMoniker* formu `Open` jde použít na počítačích Macintosh.

Můžete použít adresu URL nebo název souboru pro *lpszURL* parametru. Příklad:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- nebo –

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Viz také

[COleStreamFile – třída](../../mfc/reference/colestreamfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
