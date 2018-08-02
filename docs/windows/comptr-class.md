---
title: Comptr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 21503e38bb612f935e26f6eaaa93df2097e10445
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465334"
---
# <a name="comptr-class"></a>ComPtr – třída
Vytvoří *inteligentního ukazatele* typ, který představuje rozhraní určené typem parametru šablony. **ComPtr** automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class ComPtr;  
  
template<class T>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Rozhraní, která **ComPtr** představuje.  
  
 *U*  
 Třída, ke kterému aktuální **ComPtr** je friend. (Šablona, která používá tento parametr je chráněna.)  
  
## <a name="remarks"></a>Poznámky  
 `ComPtr<>` deklaruje typ, který představuje základního ukazatele rozhraní. Použít `ComPtr<>` deklarovat proměnnou a pak použijte šipku operátora přístupu členů (`->`) pro přístup k členská funkce rozhraní.  
  
 Další informace o inteligentních ukazatelích naleznete v tématu "Chytrých ukazatelů COM" dílčí část objektu [postupy kódování COM](http://msdn.microsoft.com/76aca556-b4d6-4e67-a2a3-4439900f0c39)v knihovně MSDN.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`InterfaceType`|Synonymum pro typ zadaný *T* parametr šablony.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtr::ComPtr – konstruktor](../windows/comptr-comptr-constructor.md)|Inicializuje novou instanci třídy **ComPtr** třídy. Přetížení poskytují výchozí, kopírovat, přesunout a převod konstruktory.|  
|[ComPtr::~ComPtr – destruktor](../windows/comptr-tilde-comptr-destructor.md)|Uvolní instanci **ComPtr**.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtr::As – metoda](../windows/comptr-as-method.md)|Vrátí **ComPtr** objekt, který představuje rozhraní identifikován parametrem určené šablony.|  
|[ComPtr::AsIID – metoda](../windows/comptr-asiid-method.md)|Vrátí **ComPtr** objekt, který představuje rozhraní, které identifikují pomocí ID zadané rozhraní.|  
|[ComPtr::AsWeak – metoda](../windows/comptr-asweak-method.md)|Získá nestálý odkaz na aktuální objekt.|  
|[ComPtr::Attach – metoda](../windows/comptr-attach-method.md)|Přidruží to **ComPtr** s typem rozhraní určeném aktuálním parametru typu šablony.|  
|[ComPtr::CopyTo – metoda](../windows/comptr-copyto-method.md)|Zkopíruje aktuální nebo zadané rozhraní přidružené k tomuto **ComPtr** na ukazatel zadaným výstupem.|  
|[ComPtr::Detach – metoda](../windows/comptr-detach-method.md)|Zruší přidružení to **ComPtr** z rozhraní, které představuje.|  
|[ComPtr::Get – metoda](../windows/comptr-get-method.md)|Načte ukazatel rozhraní, které souvisí s tímto **ComPtr**.|  
|[ComPtr::GetAddressOf – metoda](../windows/comptr-getaddressof-method.md)|Načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datový člen, který obsahuje ukazatel na rozhraní představovaného tímto rozhraním **ComPtr**.|  
|[ComPtr::ReleaseAndGetAddressOf – metoda](../windows/comptr-releaseandgetaddressof-method.md)|Uvolní rozhraní přidružené k tomuto **ComPtr** a potom načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datový člen, který obsahuje ukazatel rozhraní, která byla vydána.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Uvolní všechny odkazy pro ukazatele na rozhraní, které souvisí s tímto **ComPtr**.|  
|[ComPtr::Swap – metoda](../windows/comptr-swap-method.md)|Vymění rozhraní spravuje aktuální **ComPtr** rozhraní spravuje zadaný **ComPtr**.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtr::InternalAddRef – metoda](../windows/comptr-internaladdref-method.md)|Zvýší počet odkazů přidružený k tomuto rozhraní **ComPtr**.|  
|[ComPtr::InternalRelease – metoda](../windows/comptr-internalrelease-method.md)|Provádí operaci vydání COM pro rozhraní přidružené k tomuto **ComPtr**.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType – operátor](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Určuje, zda je či není **ComPtr** spravuje doba života objektu rozhraní.|  
|[ComPtr::operator& – operátor](../windows/comptr-operator-ampersand-operator.md)|Načte adresu aktuálního **ComPtr**.|  
|[ComPtr::operator= – operátor](../windows/comptr-operator-assign-operator.md)|Přiřadí hodnotu k aktuální **ComPtr**.|  
|[ComPtr::operator-> – operátor](../windows/comptr-operator-arrow-operator.md)|Načte ukazatel na typ určený v parametru aktuální šablony.|  
|[ComPtr::operator== – operátor](../windows/comptr-operator-equality-operator.md)|Určuje, zda dva **ComPtr** objekty rovnají.|  
|[ComPtr::operator!= – operátor](../windows/comptr-operator-inequality-operator.md)|Určuje, zda dva **ComPtr** objekty nejsou stejné.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtr::ptr_ – datový člen](../windows/comptr-ptr-data-member.md)|Obsahuje ukazatel rozhraní, který je přidružený k a spravovaného touto **ComPtr**.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)