---
title: "Třída CComPtrBase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f0d9b4d49a7568df905a595e2cf6494b2b98706d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomptrbase-class"></a>CComPtrBase – třída
Tato třída poskytuje základ pro inteligentní ukazatel třídy pomocí rutiny založené na modelu COM paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu, který bude odkazovat inteligentní ukazatel.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtrBase:: ~ CComPtrBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|Volat tuto metodu za účelem vytvoření připojení mezi `CComPtrBase`je spojovací bod a jímka klienta.|  
|[CComPtrBase::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Volat tuto metodu pro vytvoření objektu třídy přidružené k zadané ID třídy nebo ID programu.|  
|[CComPtrBase::CopyTo](#copyto)|Voláním této metody lze zkopírovat `CComPtrBase` ukazatel na jiné proměnné ukazatele.|  
|[CComPtrBase::Detach](#detach)|Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.|  
|[CComPtrBase::IsEqualObject](#isequalobject)|Volat tuto metodu za účelem zkontrolujte, zda zadaný **IUnknown** odkazuje na stejný objekt přidružený k `CComPtrBase` objektu.|  
|[CComPtrBase::QueryInterface](#queryinterface)|Voláním této metody vrátit ukazatele k zadanému rozhraní.|  
|[CComPtrBase::Release](#release)|Volejte tuto metodu za účelem uvolnění rozhraní.|  
|[CComPtrBase::SetSite](#setsite)|Volat tuto metodu a nastavit k lokalitě `CComPtrBase` do objektu **IUnknown** nadřazeného objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|Operátor přetypování.|  
|[CComPtrBase::operator!](#operator_not)|Operátor NOT.|  
|[CComPtrBase::operator &](#operator_amp)|& Operátor.|  
|[CComPtrBase::operator *](#operator_star)|* Operátor.|  
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|Je menší – než – operátor.|  
|[CComPtrBase::operator ==](#operator_eq_eq)|Operátor rovnosti.|  
|[-> CComPtrBase::operator](#operator_ptr)|Operátor ukazatelů na členy.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|Členské proměnné ukazatele data.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje základ pro další chytré ukazatele, které používají rutiny správy paměti COM, jako například [CComQIPtr](../../atl/reference/ccomqiptr-class.md) a [CComPtr](../../atl/reference/ccomptr-class.md). Přidat vlastní konstruktory a operátory odvozené třídy, ale závisí na metody poskytované `CComPtrBase`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcomcli.h  
  
##  <a name="advise"></a>CComPtrBase::Advise  
 Volat tuto metodu za účelem vytvoření připojení mezi `CComPtrBase`je spojovací bod a jímka klienta.  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 Ukazatel na klienta **IUnknown**.  
  
 `iid`  
 Identifikátor GUID spojovacího bodu. Obvykle je to stejné jako odchozí rozhraní spravuje spojovacího bodu.  
  
 `pdw`  
 Ukazatel na souboru cookie, který jednoznačně identifikuje připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [AtlAdvise](connection-point-global-functions.md#atladvise) Další informace.  
  
##  <a name="attach"></a>CComPtrBase::Attach  
 Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p2`  
 `CComPtrBase` Objektu bude převzít vlastnictví tento ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 **Připojit** volání [CComPtrBase::Release](#release) na existující [CComPtrBase::p](#p) členské proměnné a poté přiřadí `p2` k `CComPtrBase::p`. Když `CComPtrBase` objekt trvá vlastnictví ukazatel, bude automaticky volat `Release` na ukazatele, který odstraní ukazatele a všechny přidělené dat, pokud počet odkaz na objekt přejde na hodnotu 0.  
  
##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 Destruktor.  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Verze rozhraní, na kterou odkazuje `CComPtrBase`.  
  
##  <a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance  
 Volat tuto metodu pro vytvoření objektu třídy přidružené k zadané ID třídy nebo ID programu.  
  
```
HRESULT CoCreateInstance(  
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(  
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szProgID`  
 Ukazatel na ProgID, používá k obnovení CLSID.  
  
 `pUnkOuter`  
 Pokud **NULL**, vyplývá, že objekt není se vytvořila jako součást agregace. Pokud jinou hodnotu než **NULL**, je zde ukazatel na agregovaný objekt **IUnknown** rozhraní (řízení **IUnknown**).  
  
 `dwClsContext`  
 Kontext, ve kterém se spustí kód, který spravuje nově vytvořený objekt.  
  
 `rclsid`  
 CLSID související s daty a kód, který se použije k vytvoření objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch, nebo REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING nebo E_NOINTERFACE při selhání. V tématu [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) a [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) popis tyto chyby.  
  
### <a name="remarks"></a>Poznámky  
 Pokud první formulář metoda je volána, [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) slouží k obnovení CLSID. Obě forms pak zavolají [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
 V sestavení pro ladění, dojde k chybě assertion Pokud [CComPtrBase::p](#p) se nerovná na hodnotu NULL.  
  
##  <a name="copyto"></a>CComPtrBase::CopyTo  
 Voláním této metody lze zkopírovat `CComPtrBase` ukazatel na jiné proměnné ukazatele.  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *ppT*  
 Adresa proměnnou, která se zobrazí `CComPtrBase` ukazatel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu E_POINTER při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Kopie `CComPtrBase` ukazatel na *ppT*. Odkaz na spoléhat na to, [CComPtrBase::p](#p) členské proměnné se zvýší.  
  
 K chybě HRESULT bude vrácena v případě *ppT* rovná hodnotu NULL. V sestavení pro ladění, dojde k chybě assertion Pokud *ppT* rovná hodnotu NULL.  
  
##  <a name="detach"></a>CComPtrBase::Detach  
 Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vlastnictví ukazatel, nastaví [CComPtrBase::p](#p) data členské proměnné na hodnotu NULL a vrátí kopii ukazatele.  
  
##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 Volat tuto metodu za účelem zkontrolujte, zda zadaný **IUnknown** odkazuje na stejný objekt přidružený k `CComPtrBase` objektu.  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pOther`  
 **IUnknown \***  k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud objekty jsou identické, false, jinak hodnota.  
  
##  <a name="operator_not"></a>CComPtrBase::operator!  
 Operátor NOT.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud `CComHeapPtr` rovná ukazatel na hodnotu NULL, false jinak.  
  
##  <a name="operator_amp"></a>CComPtrBase::operator&amp;  
 & Operátor.  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí adresu objektu, na kterou odkazuje `CComPtrBase` objektu.  
  
##  <a name="operator_star"></a>CComPtrBase::operator *  
 * Operátor.  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu [CComPtrBase::p](#p); to znamená, ukazatel na objekt, který odkazuje `CComPtrBase` objektu.  
  
 Pokud ladicí sestavení, dojde k chybě assertion Pokud [CComPtrBase::p](#p) se nerovná na hodnotu NULL.  
  
##  <a name="operator_eq_eq"></a>CComPtrBase::operator ==  
 Operátor rovnosti.  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 Ukazatel na objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud `CComPtrBase` a *pT* bodu ke stejnému objektu, false jinak.  
  
##  <a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 Operátor ukazatele na člena.  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu [CComPtrBase::p](#p) data členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor k volání metody ve třídě, na kterou odkazuje `CComPtrBase` objektu. V sestavení pro ladění k chybě assertion dojde v případě `CComPtrBase` – datový člen odkazuje na hodnotu NULL.  
  
##  <a name="operator_lt"></a>CComPtrBase::operator&lt;  
 Je menší – než – operátor.  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 Ukazatel na objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je ukazatel spravuje aktuální objekt je menší než ukazatele, ke kterému je porovnávána.  
  
##  <a name="operator_t_star"></a>CComPtrBase::operator T *  
 Operátor přetypování.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrací ukazatel na objekt datového typu definovaného v šabloně třídy.  
  
##  <a name="p"></a>CComPtrBase::p  
 Členské proměnné ukazatele data.  
  
```
T* p;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná člena obsahuje informace ukazatele.  
  
##  <a name="queryinterface"></a>CComPtrBase::QueryInterface  
 Voláním této metody vrátit ukazatele k zadanému rozhraní.  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `Q`  
 Typ objektu, jehož rozhraní je vyžadován.  
  
 `pp`  
 Adresa výstup proměnné, která přijímá ukazatele požadované rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch nebo E_NOINTERFACE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [IUnknown::QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 V sestavení pro ladění, dojde k chybě assertion Pokud *pp* se nerovná na hodnotu NULL.  
  
##  <a name="release"></a>CComPtrBase::Release  
 Volejte tuto metodu za účelem uvolnění rozhraní.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní vydání, a [CComPtrBase::p](#p) je nastaven na hodnotu NULL.  
  
##  <a name="setsite"></a>CComPtrBase::SetSite  
 Volat tuto metodu a nastavit k lokalitě `CComPtrBase` do objektu **IUnknown** nadřazeného objektu.  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `punkParent`  
 Ukazatel **IUnknown** rozhraní nadřazeného objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
