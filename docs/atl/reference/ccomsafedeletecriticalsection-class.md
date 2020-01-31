---
title: CComSafeDeleteCriticalSection – třída
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
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821646"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection – třída

Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.

## <a name="syntax"></a>Syntaxe

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Konstruktor|
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComSafeDeleteCriticalSection:: init](#init)|Vytvoří a inicializuje objekt kritického oddílu.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritické části.|
|[CComSafeDeleteCriticalSection:: Term](#term)|Uvolní systémové prostředky používané objektem kritické části.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Označí, zda byl inicializován vnitřní objekt `CRITICAL_SECTION`.|

## <a name="remarks"></a>Poznámky

`CComSafeDeleteCriticalSection` je odvozena od třídy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). `CComSafeDeleteCriticalSection` však poskytuje další bezpečnostní mechanismy nad [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Pokud instance `CComSafeDeleteCriticalSection` přechází z oboru nebo je explicitně odstraněna z paměti, základní objekt kritického oddílu se automaticky vyčistí, pokud je stále platný. Metoda [CComSafeDeleteCriticalSection:: Term](#term) se dokončí řádným způsobem, pokud základní objekt kritického oddílu ještě není přidělený nebo už je z paměti uvolněný.

Další informace o pomocných třídách důležitých oddílů najdete v tématu [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore. h

##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Konstruktor

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen [m_bInitialized](#m_binitialized) na hodnotu NEPRAVDA.

##  <a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection

Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní vnitřní `CRITICAL_SECTION` objekt z paměti, pokud je datový člen [m_bInitialized](#m_binitialized) nastaven na hodnotu true.

##  <a name="init"></a>CComSafeDeleteCriticalSection:: init

Zavolá implementaci základní třídy [init](/visualstudio/debugger/init) a nastaví [m_bInitialized](#m_binitialized) na hodnotu true, pokud bylo úspěšné.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek [CComCriticalSection:: init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>CComSafeDeleteCriticalSection:: Lock

Volá implementaci [zámku](ccomcriticalsection-class.md#lock)základní třídy.

```
HRESULT Lock();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Poznámky

Tato metoda předpokládá, že datový člen [m_bInitialized](#m_binitialized) je po vstupu nastaven na hodnotu true. Kontrolní výraz je vygenerován v sestavení ladění, není-li tato podmínka splněna.

Další informace o chování funkce naleznete v tématu [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection:: m_bInitialized

Označí, zda byl inicializován vnitřní objekt `CRITICAL_SECTION`.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Poznámky

Datový člen `m_bInitialized` se používá ke sledování platnosti podkladového objektu `CRITICAL_SECTION` přidruženého ke třídě [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) . Pokud není tento příznak nastaven na hodnotu TRUE, nebude se podkladová `CRITICAL_SECTION` objekt pokoušet o vydání z paměti.

##  <a name="term"></a>CComSafeDeleteCriticalSection:: Term

Volá implementaci základní třídy [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term) , pokud je objekt interní `CRITICAL_SECTION` platný.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí výsledek [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)nebo S_OK, pokud [m_bInitialized](#m_binitialized) byl nastaven na hodnotu false po zadání.

### <a name="remarks"></a>Poznámky

Tuto metodu je bezpečné volat i v případě, že vnitřní objekt `CRITICAL_SECTION` není platný. Destruktor této třídy volá tuto metodu, pokud je datový člen [m_bInitialized](#m_binitialized) nastaven na hodnotu true.

## <a name="see-also"></a>Viz také:

[CComAutoCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
