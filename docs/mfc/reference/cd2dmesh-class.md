---
title: Cd2dmesh – třída
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
ms.openlocfilehash: f4ad6fd054eeb8576c2fdb2dc924f70034b3abad
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275108"
---
# <a name="cd2dmesh-class"></a>Cd2dmesh – třída

Obálka pro ID2D1Mesh.

## <a name="syntax"></a>Syntaxe

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Vytvoří objekt cd2dmesh –.|
|[CD2DMesh::~CD2DMesh](#_dtorcd2dmesh)|Destruktor. Volá se, když se likviduje objektu D2D mřížky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DMesh::Create](#create)|Vytvoří cd2dmesh –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DMesh::Destroy](#destroy)|Odstraní objekt cd2dmesh –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DMesh::Detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DMesh::Get](#get)|Vrátí ID2D1Mesh rozhraní|
|[CD2DMesh::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DMesh::Open](#open)|Otevře se síť pro naplnění.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::Operator ID2D1Mesh *](#operator_id2d1mesh_star)|Vrátí ID2D1Mesh rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|Ukazatel ID2D1Mesh.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dmesh"></a>  CD2DMesh::~CD2DMesh

Destruktor. Volá se, když se likviduje objektu D2D mřížky.

```
virtual ~CD2DMesh();
```

##  <a name="attach"></a>  CD2DMesh::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dmesh"></a>  CD2DMesh::CD2DMesh

Vytvoří objekt cd2dmesh –.

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DMesh::Create

Vytvoří cd2dmesh –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DMesh::Destroy

Odstraní objekt cd2dmesh –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DMesh::detach

Odpojí prostředků rozhraní z objektu

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DMesh::Get

Vrátí ID2D1Mesh rozhraní

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Mesh nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="isvalid"></a>  CD2DMesh::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_pmesh"></a>  CD2DMesh::m_pMesh

Ukazatel ID2D1Mesh.

```
ID2D1Mesh* m_pMesh;
```

##  <a name="open"></a>  CD2DMesh::Open

Otevře se síť pro naplnění.

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ID2D1TessellationSink, který se používá k naplnění mřížky.

##  <a name="operator_id2d1mesh_star"></a>  CD2DMesh::Operator ID2D1Mesh *

Vrátí ID2D1Mesh rozhraní

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Mesh nebo hodnota NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
