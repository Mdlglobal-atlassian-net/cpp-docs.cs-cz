---
title: Třída prostředků CD2D
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: 5e747eda42e625d0f4cf65859e471933bbb043ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369097"
---
# <a name="cd2dresource-class"></a>Třída prostředků CD2D

Abstraktní třída, která poskytuje rozhraní pro vytváření a správu prostředků D2D, jako jsou stopy, vrstvy a texty.

## <a name="syntax"></a>Syntaxe

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|Vytvoří objekt CD2DResource.|
|[ZDROJ CD2D::~CD2DResource](#_dtorcd2dresource)|Destruktor. Nazývá se při zničení objektu prostředku D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DResource::Vytvořit](#create)|Vytvoří prostředek CD2D.|
|[CD2DZdroj::Destroy](#destroy)|Zničí objekt CD2DResource.|
|[CD2DResource::IsValid](#isvalid)|Zkontroluje platnost prostředků.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DResource::isautodestroy](#isautodestroy)|Zkontrolujte, zda auto zničit vlajku.|
|[CD2DResource::Znovu vytvořit](#recreate)|Znovu vytvoří PROSTŘEDEK CD2D.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Prostředek bude zničen vlastníkem (CRenderTarget)|
|[CD2DZdroj::m_pParentTarget](#m_pparenttarget)|Ukazatel na nadřazený CRenderTarget)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>ZDROJ CD2D::~CD2DResource

Destruktor. Nazývá se při zničení objektu prostředku D2D.

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2DResource::CD2DResource

Vytvoří objekt CD2DResource.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dresourcecreate"></a><a name="create"></a>CD2DResource::Vytvořit

Vytvoří prostředek CD2D.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a>CD2DZdroj::Destroy

Zničí objekt CD2DResource.

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2DResource::isautodestroy

Zkontrolujte, zda auto zničit vlajku.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud objekt bude zničen jeho vlastníkem; jinak FALSE.

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a>CD2DResource::IsValid

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a>CD2DResource::m_bIsAutoDestroy

Prostředek bude zničen vlastníkem (CRenderTarget)

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a>CD2DZdroj::m_pParentTarget

Ukazatel na nadřazený CRenderTarget)

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a>CD2DResource::Znovu vytvořit

Znovu vytvoří PROSTŘEDEK CD2D.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
