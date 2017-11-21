---
title: "Třída CComSafeDeleteCriticalSection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs: C++
helpviewer_keywords: CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9887a64131b8e7153ca54f73007386003c87ac1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection – třída
Tato třída poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Konstruktor|  
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|Vytvoří a inicializuje objekt kritická sekce.|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritická sekce.|  
|[CComSafeDeleteCriticalSection::Term](#term)|Uvolní prostředky systému využívané objektem kritická sekce.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|Příznaky zda interní **CRITICAL_SECTION** objekt byl inicializován.|  
  
## <a name="remarks"></a>Poznámky  
 `CComSafeDeleteCriticalSection`je odvozena od třídy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Ale `CComSafeDeleteCriticalSection` nabízí v porovnání s další bezpečnostní mechanismy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  
  
 Pokud instance `CComSafeDeleteCriticalSection` ocitne mimo obor nebo je explicitně odstranit z paměti, základní objekt kritická sekce se automaticky vyčistí Pokud je stále platné. Kromě toho [CComSafeDeleteCriticalSection::Term](#term) metoda skončit řádně, je-li základní kritická sekce objekt ještě nebyl přidělen nebo už byla uvolněna z paměti.  
  
 V tématu [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) Další informace o kritická sekce pomocné třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 Konstruktor  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví [m_bInitialized](#m_binitialized) – datový člen k **false**.  
  
##  <a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection  
 Destruktor.  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní interní **CRITICAL_SECTION** objekt z paměti, pokud [m_bInitialized](#m_binitialized) – datový člen je nastaven na **true**.  
  
##  <a name="init"></a>CComSafeDeleteCriticalSection::Init  
 Volá základní třída implementace [Init](/visualstudio/debugger/init) a nastaví [m_bInitialized](#m_binitialized) k **true** v případě úspěchu.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).  
  
##  <a name="lock"></a>CComSafeDeleteCriticalSection::Lock  
Základní třída implementace volá [zámku](ccomcriticalsection-class.md#lock).  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda předpokládá [m_bInitialized](#m_binitialized) – datový člen je nastaven na **true** při vstupu. Kontrolní výrazy se generuje ve sestavení pro ladění, pokud tato condidtion není splněná.  
  
 Další informace o chování funkce, najdete v části [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized  
 Příznaky zda interní **CRITICAL_SECTION** objekt byl inicializován.  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>Poznámky  
 **M_bInitialized** – datový člen slouží ke sledování platnost základní **CRITICAL_SECTION** objekt přidružený k [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) třídy. Základní **CRITICAL_SECTION** objektu, nebude se pokus o uvolněn z paměti, pokud není tento příznak nastaven na **true**.  
  
##  <a name="term"></a>CComSafeDeleteCriticalSection::Term  
 Základní třída implementace volá [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) pokud interní **CRITICAL_SECTION** je objekt platný.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí výsledek [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), nebo **S_OK** Pokud [m_bInitialized](#m_binitialized) byla nastavena na **false** při vstupu.  
  
### <a name="remarks"></a>Poznámky  
 Je bezpečné volat i když tato metoda interní **CRITICAL_SECTION** objekt není platný. Destruktoru objektu Tato třída volá tuto metodu, pokud [m_bInitialized](#m_binitialized) – datový člen je nastaven na **true**.  
  
## <a name="see-also"></a>Viz také  
 [CComCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
