---
title: Ccomsafedeletecriticalsection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b822a76cf98acb38cd5b785a868b989a96b96a12
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879436"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Ccomsafedeletecriticalsection – třída
Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Konstruktor|  
|[Ccomsafedeletecriticalsection –:: ~ ccomsafedeletecriticalsection –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|Vytvoří a inicializuje objekt kritický oddíl.|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritický oddíl.|  
|[CComSafeDeleteCriticalSection::Term](#term)|Uvolní prostředky systému použité objektem kritický oddíl.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|Příznaky, zda vnitřní `CRITICAL_SECTION` objekt byl inicializován.|  
  
## <a name="remarks"></a>Poznámky  
 `CComSafeDeleteCriticalSection` je odvozena od třídy [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md). Ale `CComSafeDeleteCriticalSection` poskytuje další bezpečnostní mechanismy nad [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md).  
  
 Pokud instance `CComSafeDeleteCriticalSection` dostane mimo rozsah nebo je explicitně odstranit z paměti na základní objekt kritický oddíl se automaticky vyčistí Pokud je stále platný. Kromě toho [CComSafeDeleteCriticalSection::Term](#term) metoda se ukončí bez výpadku, pokud ještě nebyl přidělen na základní objekt kritický oddíl nebo již byla uvolněna z paměti.  
  
 Zobrazit [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md) Další informace o kritický oddíl pomocné třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 Konstruktor  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví [m_bInitialized](#m_binitialized) datový člen na hodnotu FALSE.  
  
##  <a name="dtor"></a>  Ccomsafedeletecriticalsection –:: ~ ccomsafedeletecriticalsection –  
 Destruktor.  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vnitřní `CRITICAL_SECTION` objekt z paměti by [m_bInitialized](#m_binitialized) datový člen je nastavena na hodnotu TRUE.  
  
##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init  
 Volá implementaci základní třídy [Init](/visualstudio/debugger/init) a nastaví [m_bInitialized](#m_binitialized) na hodnotu TRUE v případě úspěšného ověření.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).  
  
##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock  
Volá implementaci základní třídy [Zámek](ccomcriticalsection-class.md#lock).  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda předpokládá, [m_bInitialized](#m_binitialized) datový člen je nastavena na hodnotu TRUE při vstupu. Pokud tento condidtion nedosáhne, vygeneruje se kontrolní výraz v sestaveních ladění.  
  
 Další informace o chování funkce, najdete [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized  
 Příznaky, zda vnitřní `CRITICAL_SECTION` objekt byl inicializován.  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>Poznámky  
 `m_bInitialized` Datový člen se používá ke sledování platnosti základní `CRITICAL_SECTION` objekt přidružený k [ccomsafedeletecriticalsection –](../../atl/reference/ccomsafedeletecriticalsection-class.md) třídy. Základní `CRITICAL_SECTION` objektu nesmí dojít k pokusu uvolnit z paměti, není-li tento příznak nastaven na hodnotu TRUE.  
  
##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term  
 Volá implementaci základní třídy [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) pokud vnitřní `CRITICAL_SECTION` objektu je neplatný.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), nebo hodnotu S_OK Pokud [m_bInitialized](#m_binitialized) byla nastavena na hodnotu FALSE, při vstupu.  
  
### <a name="remarks"></a>Poznámky  
 Je bezpečné volat tuto metodu i v případě interní `CRITICAL_SECTION` objekt není platný. Destruktor tuto třídu volá tuto metodu, pokud [m_bInitialized](#m_binitialized) datový člen je nastavena na hodnotu TRUE.  
  
## <a name="see-also"></a>Viz také  
 [Ccomautocriticalsection – třída](../../atl/reference/ccomcriticalsection-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
