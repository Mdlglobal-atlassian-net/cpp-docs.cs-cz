---
title: CComSafeDeleteCriticalSection Třída
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327372"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection Třída

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritické části.

## <a name="syntax"></a>Syntaxe

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomsafeDeleteCriticalSection::CcomsafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Konstruktor|
|[CcomSafeDeleteCriticalSection::~ccomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection Ccom](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Vytvoří a inicializuje objekt kritického řezu.|
|[CComSafeDeleteCriticalSection::Zámek](#lock)|Získá vlastnictví objektu kritické části.|
|[CComSafeDeleteCriticalSection::Termín](#term)|Uvolní systémové prostředky používané objektem kritické části.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Označí, `CRITICAL_SECTION` zda byl vnitřní objekt inicializován.|

## <a name="remarks"></a>Poznámky

`CComSafeDeleteCriticalSection`pochází z třídy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Poskytuje `CComSafeDeleteCriticalSection` však další bezpečnostní mechanismy než [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Pokud instance `CComSafeDeleteCriticalSection` přejde mimo rozsah nebo je explicitně odstraněn z paměti, základní objekt kritické části bude automaticky vyčištěn, pokud je stále platný. Kromě toho [CComSafeDeleteCriticalSection::Term](#term) metoda bude řádně ukončena, pokud základní objekt kritické části ještě nebyla přidělena nebo již byla uvolněna z paměti.

Další informace o třídách pomocníků kritické části naleznete v části [CComCriticalSection.](../../atl/reference/ccomcriticalsection-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Ccomcriticalsekce](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CcomsafeDeleteCriticalSection::CcomsafeDeleteCriticalSection

Konstruktor

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen [m_bInitialized](#m_binitialized) na HODNOTU NEPRAVDA.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CcomSafeDeleteCriticalSection::~ccomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection CcomSafeDeleteCriticalSection Ccom

Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní vnitřní `CRITICAL_SECTION` objekt z paměti, pokud je datový člen [m_bInitialized](#m_binitialized) nastaven na hodnotu TRUE.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafeDeleteCriticalSection::Init

Volá implementaci základní třídy [Init](/visualstudio/debugger/init) a nastaví [m_bInitialized](#m_binitialized) na HODNOTU TRUE, pokud je úspěšná.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek [cComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafeDeleteCriticalSection::Zámek

Volá implementaci základní třídy [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek [cComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Poznámky

Tato metoda předpokládá, že [m_bInitialized](#m_binitialized) datový člen je při zadávání nastaven na hodnotu TRUE. Kontrolní výraz je generován v sestavení ladění, pokud tato podmínka není splněna.

Další informace o chování funkce naleznete v části [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized

Označí, `CRITICAL_SECTION` zda byl vnitřní objekt inicializován.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Poznámky

Datový `m_bInitialized` člen se používá ke sledování `CRITICAL_SECTION` platnosti základního objektu přidruženého ke třídě [CComSafeDeleteCriticalSection.](../../atl/reference/ccomsafedeletecriticalsection-class.md) Základní `CRITICAL_SECTION` objekt nebude pokus o uvolnění z paměti, pokud tento příznak není nastaven na hodnotu TRUE.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafeDeleteCriticalSection::Termín

Volá implementaci základní třídy [CComCriticalSection::Term,](../../atl/reference/ccomcriticalsection-class.md#term) pokud je platný vnitřní `CRITICAL_SECTION` objekt.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek [cComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)nebo S_OK pokud [byl m_bInitialized](#m_binitialized) při zadávání nastaven na hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Je bezpečné volat tuto metodu `CRITICAL_SECTION` i v případě, že vnitřní objekt není platný. Destruktor této třídy volá tuto metodu, pokud je datový člen [m_bInitialized](#m_binitialized) nastaven na hodnotu TRUE.

## <a name="see-also"></a>Viz také

[Třída CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
