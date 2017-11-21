---
title: "Třída CAdapt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
dev_langs: C++
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 37ce02b9493c47a2c93d9e54e14f73b5c980317d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cadapt-class"></a>CAdapt – třída
Tato šablona se používá k zabalení tříd, které mění definici operátoru address-of tak, aby vracely něco jiného než adresu objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CAdapt
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Adaptovaný typ  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAdapt::CAdapt](#cadapt)|Konstruktor|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAdapt::operator const T &](#operator_const_t_amp)|Vrátí `const` odkaz na `m_T`.|  
|[CAdapt::operator T &](#operator_t_amp)|Vrátí odkaz na `m_T`.|  
|[CAdapt::operator <](#operator_lt)|Porovná objekt přizpůsobena typu s `m_T`.|  
|[CAdapt::operator =](#operator_eq)|Přiřadí objekt typu přizpůsobena `m_T`.|  
|[CAdapt::operator ==](#operator_eq_eq)|Porovná objekt přizpůsobena typu s `m_T`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAdapt::m_T](#m_t)|Adaptovaná data|  
  
## <a name="remarks"></a>Poznámky  
 `CAdapt`je jednoduchou šablonu slouží k zabalení třídy, které znovu definovat address-of – operátor ( `operator &`) vrátit něco jiného než adresu objektu. Příklady takových třídy ATL na `CComBSTR`, `CComPtr`, a `CComQIPtr` třídy a třídy podpory kompilátoru modelu COM, `_com_ptr_t`. Tyto třídy všechny definovat operátor adresy pro zpáteční adresa jednoho z jejich datové členy ( `BSTR` u `CComBSTR`a v případě jiné třídy ukazatele rozhraní).  
  
 `CAdapt`na primární role je skrýt operátor adresy definované třídou `T`, ještě stále si zachovat vlastnosti přizpůsobena třídy. `CAdapt`splňuje tato role tím, že se členem veřejné [m_T](#m_t), typu `T`a tak, že definujete operátory převodu, relační operátory a kopírovacího konstruktoru povolit specializací `CAdapt` být zpracována jako v případě, že jsou objekty typu `T`.  
  
 Třída adaptér `CAdapt` je užitečné, protože některé třídy stylu kontejneru očekávají, že moct získat adresy jejich obsažených objektů pomocí operátoru adresy. Změna definice operátoru address-of může tento požadavek zmařit a zpravidla způsobí chyby kompilace a zabrání použití neadaptovaného typu s třídami, které očekávají, že bude fungovat. `CAdapt`poskytuje způsob, jak chcete vyřešit tyto problémy.  
  
 Obvykle použijete `CAdapt` když chcete uložit `CComBSTR`, `CComPtr`, `CComQIPtr`, nebo `_com_ptr_t` objekty ve třídě stylu kontejneru. To se nejčastěji potřebné pro podporu standardu C ++ 11 před kontejnery standardní knihovna C++, ale C ++ 11 standardní knihovna kontejnery automaticky pracovat s typy, které mají přetížený `operator&()`. Standardní knihovna dosahuje interně pomocí [std::addressof](../../standard-library/memory-functions.md#addressof) získat true adresy objektů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcomcli.h  
  
##  <a name="cadapt"></a>CAdapt::CAdapt  
 Konstruktory povolit objekt adaptéru tak, aby se výchozí sestavený, zkopírovaných z objektu typu přizpůsobena nebo zkopírovaných z jiného objektu adaptéru.  
  
```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Proměnná typu přizpůsobována zkopírují do nově vytvořený adaptér objektu.  
  
 *rSrCA*  
 Adaptér objekt, jehož obsažené data by měla být zkopírován (nebo přesunout) do nově vytvořený adaptér objektu.  
  
##  <a name="m_t"></a>CAdapt::m_T  
 Obsahuje data, přizpůsobován.  
  
```
T m_T;
```  
  
### <a name="remarks"></a>Poznámky  
 To **veřejné** – datový člen lze přistupovat přímo nebo nepřímo s [operátor const T &](#operator_const_t_amp) a [operator T &](#operator_t_amp).  
  
##  <a name="operator_const_t_amp"></a>CAdapt::operator const T&amp;  
 Vrátí **const** odkaz na [m_T](#m_t) člena, což adaptér objekt, který má být zpracován, jako by měla objekt typu `T`.  
  
```  
operator const T&() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **const** odkaz na `m_T`.  
  
##  <a name="operator_t_amp"></a>CAdapt::operator T&amp;  
 Vrátí odkaz na [m_T](#m_t) člena, což adaptér objekt, který má být zpracován, jako by měla objekt typu `T`.  
  
```  
operator T&();
```     
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `m_T`.  
  
##  <a name="operator_lt"></a>CAdapt::operator&lt;  
 Porovná objekt přizpůsobena typu s [m_T](#m_t).  
  
```
bool operator<(const T& rSrc) const;
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odkaz na objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek porovnání mezi `m_T` a `rSrc`.  
  
##  <a name="operator_eq"></a>CAdapt::operator =  
 Operátor přiřazení přiřadí argument, `rSrc`, se data členem [m_T](#m_t) a vrátí aktuální objekt adaptéru.  
  
```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odkaz na objekt přizpůsobena typu, který se má zkopírovat. 

 `rSrCA`Odkaz na objekt, který chcete přesunout. 
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální objekt.  
  
##  <a name="operator_eq_eq"></a>CAdapt::operator ==  
 Porovná objekt přizpůsobena typu s [m_T](#m_t).  
  
```
bool operator== (const T& rSrc) const;
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odkaz na objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek porovnání mezi `m_T` a `rSrc`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
