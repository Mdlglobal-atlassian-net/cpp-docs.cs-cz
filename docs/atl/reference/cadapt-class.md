---
title: Cadapt – třída
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 39184e952475fa0f05a6fc25c433191ea22b5c16
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269822"
---
# <a name="cadapt-class"></a>Cadapt – třída

Tato šablona se používá k zabalení tříd, které mění definici operátoru address-of tak, aby vracely něco jiného než adresu objektu.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Adaptovaný typ

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAdapt::operator const T &](#operator_const_t_amp)|Vrátí **const** odkaz na `m_T`.|
|[CAdapt::operator T &](#operator_t_amp)|Vrátí odkaz na `m_T`.|
|[CAdapt::operator <](#operator_lt)|Porovná objekt adaptovaného typu s `m_T`.|
|[CAdapt::operator =](#operator_eq)|Přiřadí objekt adaptovaného typu k `m_T`.|
|[CAdapt::operator ==](#operator_eq_eq)|Porovná objekt adaptovaného typu s `m_T`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Adaptovaná data|

## <a name="remarks"></a>Poznámky

`CAdapt` je jednoduchá šablona slouží k zabalení tříd, které mění definici operátoru address-of (`operator &`) k vracely něco jiného než adresu objektu. Mezi příklady těchto tříd patří ATL `CComBSTR`, `CComPtr`, a `CComQIPtr` třídy a třídy podpory kompilátoru modelu COM, `_com_ptr_t`. Všechny tyto třídy mění definici operátoru z adresy vrátí adresu jednoho ze svých datových členů (v případě třídy BSTR `CComBSTR`a ukazatel rozhraní v případě jiných tříd).

`CAdapt`v primární roli je skrýt operátor address-of definovaný třídou *T*, ale stále zachovat charakteristiky této adaptované třídy. `CAdapt` splňuje tuto roli tak, že veřejný člen [m_T](#m_t), typu *T*a tak, že definujete operátory převodu, operátory porovnání a kopírovacího konstruktoru povolit specializace `CAdapt` bude zacházeno, jako kdyby byly objekty typu *T*.

Třída adaptéru `CAdapt` je užitečné, protože některé kontejnerové třídy očekávají, že budete moci získat adresy svých obsažených objektů pomocí operátoru address-of. Změna definice operátoru address-of může tento požadavek zmařit a zpravidla způsobí chyby kompilace a zabrání použití neadaptovaného typu s třídami, které očekávají, že bude fungovat. `CAdapt` poskytuje způsob řešení těchto problémů.

Obvykle budete používat `CAdapt` kdy budete chtít ukládat `CComBSTR`, `CComPtr`, `CComQIPtr`, nebo `_com_ptr_t` ve třídě kontejnerové objekty. To se běžně potřebné pro standardní knihovny C++ kontejnery před podporou standardu C ++ 11, ale C ++ 11 kontejnery standardní knihovny automaticky fungují s typy, které přetěžují `operator&()`. Standardní knihovna toho dosahuje interně pomocí [std::addressof](../../standard-library/memory-functions.md#addressof) k získává skutečné adresy objektů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

##  <a name="cadapt"></a>  CAdapt::CAdapt

Konstruktory povolit adaptér objektu jako výchozí vytvořený, zkopírovány z objekt adaptovaného typu nebo zkopírovaných z jiného objektu adaptér.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Proměnné typu adaptovaná zkopírovat do objektu nově vytvořeného adaptéru.

*rSrCA*<br/>
Objekt adaptér jehož dat obsažených by měl zkopírovat (nebo přesunut) do nově vytvořeného adaptér objektu.

##  <a name="m_t"></a>  CAdapt::m_T

Obsahuje adaptovaná data.

```
T m_T;
```

### <a name="remarks"></a>Poznámky

To **veřejné** datový člen lze přistupovat přímo nebo nepřímo pomocí [operátor const T &](#operator_const_t_amp) a [operator T &](#operator_t_amp).

##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;

Vrátí **const** odkaz [m_T](#m_t) člena, což objekt adaptér, který má zacházet, jako by šlo objekt typu *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** odkaz na `m_T`.

##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;

Vrátí odkaz na [m_T](#m_t) člena, což objekt adaptér, který má zacházet, jako by šlo objekt typu *T*.

```
operator T&();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `m_T`.

##  <a name="operator_lt"></a>  CAdapt::operator &lt;

Porovná objekt adaptovaného typu s [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Výsledek porovnání mezi `m_T` a *rSrc*.

##  <a name="operator_eq"></a>  CAdapt::operator =

Operátor přiřazení přiřazuje argumentu *rSrc*, na datový člen [m_T](#m_t) a vrátí aktuální objekt adaptéru.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt adaptovaného typu, které se mají zkopírovat.

*rSrCA*<br/>
Odkaz na objekt přesunout.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální objekt.

##  <a name="operator_eq_eq"></a>  CAdapt::operator ==

Porovná objekt adaptovaného typu s [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Výsledek porovnání mezi *m_T* a *rSrc*.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
