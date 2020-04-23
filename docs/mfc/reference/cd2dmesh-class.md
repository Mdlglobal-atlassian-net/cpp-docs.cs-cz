---
title: CD2DMesh – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: eaecdb6ba6f1382f16177e0567b31c9fd09da6ff
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753091"
---
# <a name="cd2dmesh-class"></a>CD2DMesh – třída

Obálka pro ID2D1Mesh.

## <a name="syntax"></a>Syntaxe

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Vytvoří objekt CD2DMesh.|
|[CD2DMesh::~CD2DMesh](#_dtorcd2dmesh)|Destruktor. Nazývá se při zničení objektu sítě D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DMesh::Vytvořit](#create)|Vytvoří cd2DMesh. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Zničí objekt CD2DMesh. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DMesh::Získat](#get)|Vrátí rozhraní ID2D1Mesh.|
|[CD2DMesh::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Otevřít](#open)|Otevře síť pro plnění.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::operátor ID2D1Mesh*](#operator_id2d1mesh_star)|Vrátí rozhraní ID2D1Mesh.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Ukazatel na ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a>CD2DMesh::~CD2DMesh

Destruktor. Nazývá se při zničení objektu sítě D2D.

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a>CD2DMesh::Připojit

Připojí k objektu existující rozhraní prostředků.

```cpp
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a>CD2DMesh::CD2DMesh

Vytvoří objekt CD2DMesh.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dmeshcreate"></a><a name="create"></a>CD2DMesh::Vytvořit

Vytvoří cd2DMesh.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a>CD2DMesh::Destroy

Zničí objekt CD2DMesh.

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a>CD2DMesh::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dmeshget"></a><a name="get"></a>CD2DMesh::Získat

Vrátí rozhraní ID2D1Mesh.

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Mesh nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a>CD2DMesh::IsValid

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a>CD2DMesh::m_pMesh

Ukazatel na ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a>CD2DMesh::Otevřít

Otevře síť pro plnění.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ID2D1TessellationSink, který se používá k naplnění sítě.

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a>CD2DMesh::operátor ID2D1Mesh*

Vrátí rozhraní ID2D1Mesh.

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Mesh nebo NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
