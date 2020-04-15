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
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319772"
---
# <a name="cmonikerfile-class"></a>CMonikerFile – třída

Představuje datový proud ( [IStream)](/windows/win32/api/objidl/nn-objidl-istream)pojmenovaný [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker).

## <a name="syntax"></a>Syntaxe

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Vytvoří `CMonikerFile` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMonikerFile::Zavřít](#close)|Odpojí a uvolní datový proud a uvolní zástupný název.|
|[CMonikerFile::Detach](#detach)|Odpojí `IMoniker` od tohoto `CMonikerFile` objektu.|
|[CMonikerFile::GetMoniker](#getmoniker)|Vrátí aktuální zástupné soubory.|
|[CMonikerFile::Otevřít](#open)|Otevře zadaný soubor pro získání datového proudu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Získá kontext vazby nebo vytvoří výchozí inicializovaný kontext vazby.|

## <a name="remarks"></a>Poznámky

Zástupný název obsahuje informace podobné jako cesta k souboru. Pokud máte ukazatel na `IMoniker` rozhraní objektu zástupný název, můžete získat přístup k identifikovanému souboru bez jakékoli další konkrétní informace o tom, kde je soubor skutečně umístěn.

Odvozené `COleStreamFile`z `CMonikerFile` , trvá zástupný název nebo reprezentace řetězce může vytvořit do zástupný název a váže na datový proud, pro který zástupný název je název. Potom můžete číst a zapisovat do tohoto datového proudu. Skutečným účelem `CMonikerFile` je poskytnout jednoduchý `IStream`přístup `IMoniker`k s pojmenované s tak, že není třeba `CFile` vázat na datový proud sami, ale mají funkce pro datový proud.

`CMonikerFile`nelze použít k navázání na nic jiného než na datový proud. Pokud chcete vytvořit vazbu na úložiště nebo `IMoniker` objekt, musíte použít rozhraní přímo.

Další informace o datových proudech a zástupcích naleznete v [tématu COleStreamFile](../../mfc/reference/colestreamfile-class.md) v *odkaz knihovny MFC* a [IStream](/windows/win32/api/objidl/nn-objidl-istream) a [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMonikerFile::Zavřít

Volání této funkce odpojit a uvolnit datový proud a uvolnit zástupný název.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Lze volat na neotevřené nebo již uzavřené datové proudy.

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

Vytvoří `CMonikerFile` objekt.

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>CMonikerFile::CreateBindContext

Volání této funkce k vytvoření výchozího inicializovaného kontextu vazby.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parametry

*chyba*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na kontext vazby [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) svázat s pokud je úspěšný; jinak NULL. Pokud instance byla otevřena s rozhraním, `IBindHost` kontext `IBindHost`vazby je načten z . Pokud neexistuje `IBindHost` žádné rozhraní nebo rozhraní se nezdaří vrátit kontext vazby, je vytvořen kontext vazby. Popis rozhraní [IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) naleznete v souboru Windows SDK.

### <a name="remarks"></a>Poznámky

Kontext vazby je objekt, který ukládá informace o operaci vazby konkrétní zástupný název. Tuto funkci můžete přepsat a poskytnout vlastní kontext vazby.

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMonikerFile::Detach

Volání této funkce zavřete datový proud.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*chyba*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMonikerFile::GetMoniker

Volání této funkce načíst ukazatel na aktuální zástupný název.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální zástupný název rozhraní ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, `CMonikerFile` že není rozhraní, vrácený ukazatel nezvýší počet odkazů (prostřednictvím [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)) a zástupný název je uvolněna při uvolnění objektu. `CMonikerFile` Pokud si chcete zástupnou přezdívku podržet nebo ji `AddRef` uvolnit sami, musíte ji uvolnit.

## <a name="cmonikerfileopen"></a><a name="open"></a>CMonikerFile::Otevřít

Volání této členské funkce otevřete soubor nebo objekt zástupný název.

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

*chyba*<br/>
Ukazatel na výjimku souboru. V případě chyby bude nastavena na příčinu.

*pMoniker*<br/>
Ukazatel na rozhraní `IMoniker` zástupný název, který má být použit k získání datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Parametr *lpszURL* nelze použít v systému Macintosh. Pouze *pMoniker* forma `Open` lze použít na Macintosh.

Pro parametr *lpszURL* můžete použít adresu URL nebo název souboru. Příklad:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\-nebo -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Viz také

[COleStreamFile – třída](../../mfc/reference/colestreamfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
