---
title: "Třída CComEnumImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
dev_langs: C++
helpviewer_keywords: CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ecc87bf670f56a2f56246cf45d2819b7ab7841f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl – třída
Tato třída poskytuje implementaci pro rozhraní modelu COM enumerátor ve výčtu jsou umístění v matici.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy>  
class ATL_NO_VTABLE CComEnumImpl : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Enumerátor COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) rozhraní.  
  
 `piid`  
 Ukazatel na hodnotu Identifikátoru rozhraní enumerátor.  
  
 `T`  
 Typ položky, které jsou vystavené rozhraní enumerátor.  
  
 `Copy`  
 Homogenní [zkopírujte zásady třída](../../atl/atl-copy-policy-classes.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor|  
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComEnumImpl::Clone](#clone)|Implementace [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[CComEnumImpl::Init](#init)|Inicializuje enumerátor.|  
|[CComEnumImpl::Next](#next)|Implementace [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[CComEnumImpl::Reset](#reset)|Implementace [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[CComEnumImpl::Skip](#skip)|Implementace [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComEnumImpl::m_begin](#m_begin)|Ukazatel na první položku v poli.|  
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Zkopírujte příznaky předána `Init`.|  
|[CComEnumImpl::m_end](#m_end)|Ukazatel na umístění bezprostředně za poslední položky v poli.|  
|[CComEnumImpl::m_iter](#m_iter)|Ukazatel na aktuální položky v poli.|  
|[CComEnumImpl::m_spUnk](#m_spunk)|**IUnknown** ukazatele objektu poskytuje kolekci ve výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComEnumImpl`poskytuje implementaci pro rozhraní modelu COM enumerátor ve výčtu jsou umístění v matici. Tato třída je obdobou `IEnumOnSTLImpl` třídy, která představuje implementaci objektu enumerátor rozhraní založené na kontejner standardní knihovna C++.  
  
> [!NOTE]
>  Podrobnosti o další rozdíly mezi `CComEnumImpl` a `IEnumOnSTLImpl`, najdete v části [CComEnumImpl::Init](#init).  
  
 Obvykle bude *není* muset vytvořit vlastní Enumerátor třídy odvozené z této implementaci rozhraní. Pokud chcete použít enumerátor ATL zadaný na základě pole, je dnes běžné k vytvoření instance [CComEnum](../../atl/reference/ccomenum-class.md).  
  
 Ale pokud potřebujete zajistit vlastní enumerátor, (například jeden, který zveřejňuje rozhraní kromě rozhraní enumerátor), můžete odvozovat z této třídy. V takovém případě je pravděpodobné, že budete potřebovat k přepsání [CComEnumImpl::Clone](#clone) metody můžete zajistit vlastní implementaci.  
  
 Další informace najdete v tématu [ATL – kolekce a výčty](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComEnumImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl  
 Konstruktor  
  
```
CComEnumImpl();
```  
  
##  <a name="dtor"></a>CComEnumImpl:: ~ CComEnumImpl  
 Destruktor.  
  
```
~CComEnumImpl();
```  
  
##  <a name="init"></a>CComEnumImpl::Init  
 Tato metoda musí volat před předáním ukazatele rozhraní enumerátor zpět na všechny klienty.  
  
```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```  
  
### <a name="parameters"></a>Parametry  
 *začít*  
 Ukazatel na první prvek pole obsahující položky, které chcete vytvořit její výčet.  
  
 `end`  
 Ukazatel na umístění bezprostředně za posledním elementem pole obsahující položky, které chcete vytvořit její výčet.  
  
 *pUnk*  
 [v] **IUnknown** ukazatele objektu, který musí být zachováno po dobu životnosti enumerátor. Předat **NULL** Pokud takový objekt existuje.  
  
 `flags`  
 Příznaky určující, zda by měl enumerátor převzít vlastnictví pole nebo vytvořit si kopii. Možné hodnoty jsou popsané níže.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu pouze jednou – inicializovat enumerátor, použít a pak ji rychle výjimku.  
  
 Pokud předáte ukazatele položky v poli uchovávat v jiném objektu (a neptat enumerátor ke zkopírování dat), můžete použít *pUnk* parametr zajistit, že jsou k dispozici pro stejně dlouho jako enumerátor objekt a pole drží je potřebuje. Enumerátor jednoduše obsahuje COM odkaz na objekt pro zachování připojení. Odkaz na COM automaticky vydání při enumerátor zničena.  
  
 `flags` Parametr umožňuje určit, jak by měly enumerátor zpracovávat elementy pole do ní předán. `flags`můžete provést jednu z hodnot z **CComEnumFlags** výčtu vidíte níže:  
  
```  
enum CComEnumFlags  
   {  
   AtlFlagNoCopy = 0,  
   AtlFlagTakeOwnership = 2, // BitOwn  
   AtlFlagCopy = 3           // BitOwn | BitCopy  
   };  
```  
  
 **AtlFlagNoCopy** rozumí doba platnosti tohoto pole není řízen enumerátor. V takovém případě buď pole bude statické nebo objekt identifikovaný *pUnk* je zodpovědná za uvolnění pole, když už ho nepotřebují.  
  
 **AtlFlagTakeOwnership** znamená, že odstraňování pole je kontrolován enumerátor. V takovém případě pole musí mít byla přidělí dynamicky pomocí **nové**. Enumerátor odstraní pole v jeho destruktor. Obvykle byste předáte **NULL** pro *pUnk*, i když stále můžete předat platný ukazatel Pokud budete muset být informováni o zničení enumerátor z nějakého důvodu.  
  
 **AtlFlagCopy** znamená, že nové pole je potřeba vytvořit kopírování pole předaný `Init`. Doba platnosti nové pole je kontrolován enumerátor. Enumerátor odstraní pole v jeho destruktor. Obvykle byste předáte **NULL** pro *pUnk*, i když stále můžete předat platný ukazatel Pokud budete muset být informováni o zničení enumerátor z nějakého důvodu.  
  
> [!NOTE]
>  Prototyp tato metoda určuje, že je typu prvků pole **T**, kde **T** byl definován jako parametr šablony k třídě. Toto je stejný typ, který je zveřejněný prostřednictvím metody rozhraní COM [CComEnumImpl::Next](#next). Vyplývá tohoto předpokládají, že na rozdíl od [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), tato třída nepodporuje jiného úložiště a datové typy viditelné. Datový typ elementů v poli musí být stejný jako datový typ, který je zveřejněný prostřednictvím rozhraní modelu COM.  
  
##  <a name="clone"></a>CComEnumImpl::Clone  
 Tato metoda poskytuje implementace [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) metoda tak, že vytvoříte objekt typu `CComEnum`, inicializace stejným pole a iterator používá aktuální objekt nebo vrátit rozhraní na nově vytvořený objekt.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Enumerátor rozhraní na nově vytvořený objekt klonovat z aktuální enumerátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Klonovaný výčty nikdy provádět vlastní kopii (nebo převzít vlastnictví) dat používá původní enumerátor. V případě potřeby klonovaný výčty ponechá původní enumerátor zachování připojení (pomocí odkazu COM) k zajištění, že data nejsou k dispozici pro tak dlouho, dokud je potřebují.  
  
##  <a name="m_spunk"></a>CComEnumImpl::m_spUnk  
 Ukazatel this inteligentní udržuje odkaz na objekt předaný [CComEnumImpl::Init](#init), zajistíte, aby zůstala aktivní po dobu životnosti enumerátor.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
##  <a name="m_begin"></a>CComEnumImpl::m_begin  
 Ukazatel na umístění bezprostředně za posledním elementem pole obsahující položky, které chcete vytvořit její výčet.  
  
```
T* m_begin;
```  
  
##  <a name="m_end"></a>CComEnumImpl::m_end  
 Ukazatel na první prvek pole obsahující položky, které chcete vytvořit její výčet.  
  
```
T* m_end;
```  
  
##  <a name="m_iter"></a>CComEnumImpl::m_iter  
 Ukazatel na aktuálního elementu pole obsahující položky, které chcete vytvořit její výčet.  
  
```
T* m_iter;
```  
  
##  <a name="m_dwflags"></a>CComEnumImpl::m_dwFlags  
 V příznacích předaný [CComEnumImpl::Init](#init).  
  
```
DWORD m_dwFlags;
```  
  
##  <a name="next"></a>CComEnumImpl::Next  
 Tato metoda poskytuje implementace [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) metoda.  
  
```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet elementů požadovaný.  
  
 `rgelt`  
 [out] Pole, které mají být vyplněny elementy.  
  
 `pceltFetched`  
 [out] Počet elementů ve skutečnosti, vrátí se v `rgelt`. To může být menší než `celt` Pokud méně než `celt` prvků zůstávaly v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="reset"></a>CComEnumImpl::Reset  
 Tato metoda poskytuje implementace [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) metoda.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="skip"></a>CComEnumImpl::Skip  
 Tato metoda poskytuje implementace [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) metoda.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet elementů tak, aby přeskočil.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vrátí hodnotu E_INVALIDARG `celt` rovná nule, vrátí S_FALSE, pokud menší než `celt` elementy jsou vráceny, v opačném případě vrátí S_OK.  
  
## <a name="see-also"></a>Viz také  
 [IEnumOnSTLImpl – třída](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum – třída](../../atl/reference/ccomenum-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
