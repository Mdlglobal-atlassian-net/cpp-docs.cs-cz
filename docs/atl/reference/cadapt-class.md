---
title: Třída CAdapt
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
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321632"
---
# <a name="cadapt-class"></a>Třída CAdapt

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

|Name (Název)|Popis|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAdapt::operátor const T&](#operator_const_t_amp)|Vrátí **odkaz na const** . `m_T`|
|[CAdapt::operátor T&](#operator_t_amp)|Vrátí odkaz `m_T`na .|
|[CAdapt::<operátoru](#operator_lt)|Porovná objekt upraveného typu `m_T`s .|
|[CAdapt::operátor =](#operator_eq)|Přiřadí objekt upraveného typu `m_T`.|
|[CAdapt::operátor ==](#operator_eq_eq)|Porovná objekt upraveného typu `m_T`s .|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Adaptovaná data|

## <a name="remarks"></a>Poznámky

`CAdapt`je jednoduchá šablona používaná k zalomení`operator &`tříd, které předefinují operátor address-of ( ) a vrátí něco jiného než adresu objektu. Příklady `CComBSTR`těchto tříd zahrnují atl `CComPtr`, `CComQIPtr` a třídy a třídy `_com_ptr_t`kompilátoru COM podporu třídy . Tyto třídy všechny předefinovat operátor address-of vrátit adresu jednoho z jejich datových `CComBSTR`členů (BSTR v případě , a ukazatel rozhraní v případě ostatních tříd).

`CAdapt`'s primární úlohou je skrýt adresu operátora definovaného třídou *T*, ale stále zachovat vlastnosti upravené třídy. `CAdapt`plní tuto úlohu tím, že drží veřejného [člena, m_T](#m_t), typu *T*, a definováním operátorů `CAdapt` převodu, operátorů porovnání a konstruktoru kopie, aby se specializace mise mohly zacházet, jako by se jednalo o objekty typu *T*.

Třída adaptéru `CAdapt` je užitečná, protože některé třídy stylu kontejneru očekávají, že budou moci získat adresy svých obsažených objektů pomocí operátoru address-of. Změna definice operátoru address-of může tento požadavek zmařit a zpravidla způsobí chyby kompilace a zabrání použití neadaptovaného typu s třídami, které očekávají, že bude fungovat. `CAdapt`poskytuje způsob, jak tyto problémy obejít.

Obvykle použijete, `CAdapt` když chcete uložit `CComBSTR` `CComPtr`, `CComQIPtr`, `_com_ptr_t` , nebo objekty ve třídě stylu kontejneru. To bylo nejčastěji nezbytné pro kontejnery standardní knihovny C++ před podporou standardu C++ 11, ale kontejnery `operator&()`standardní knihovny C++ 11 automaticky pracují s typy, které mají přetížené . Standardní knihovna toho dosahuje interním použitím [std::addressof](../../standard-library/memory-functions.md#addressof) k získání skutečných adres objektů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

Konstruktory umožňují, aby byl objekt adaptéru ve výchozím nastavení vytvořen, zkopírován z objektu upraveného typu nebo zkopírován z jiného objektu adaptéru.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Proměnná typu upravovaného pro kopírování do nově postaveného objektu adaptéru.

*rSrCA*<br/>
Objekt adaptéru, jehož obsažená data by měla být zkopírována (nebo přesunuta) do nově vytvořeného objektu adaptéru.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt::m_T

Obsahuje data upravována.

```
T m_T;
```

### <a name="remarks"></a>Poznámky

K tomuto **veřejnému** datovému členu se přímo nebo nepřímo přistupuje [operátor Const T&](#operator_const_t_amp) a operátor T [&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt::operátor const T&amp;

Vrátí **const** odkaz na [m_T](#m_t) člen, který umožňuje objekt adaptéru, který má být zpracován, jako by byl objekt typu *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const** odkaz `m_T`na .

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt::operátor T&amp;

Vrátí odkaz na [m_T](#m_t) člen, který umožňuje, aby byl objekt adaptéru považován za objekt typu *T*.

```
operator T&();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt::operátor&lt;

Porovná objekt upraveného typu s [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Výsledek porovnání mezi `m_T` a *rSrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt::operátor =

Operátor přiřazení přiřadí argument *rSrc*m_T datového [člena](#m_t) a vrátí aktuální objekt adaptéru.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt upraveného typu, který má být zkopírován.

*rSrCA*<br/>
Odkaz na objekt, který má být přesunut.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální objekt.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt::operátor ==

Porovná objekt upraveného typu s [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Výsledek porovnání mezi *m_T* a *rSrc*.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
