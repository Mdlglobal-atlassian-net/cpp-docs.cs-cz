---
title: "ComPtr – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr
dev_langs: C++
helpviewer_keywords: ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96b46fe15b2c101ed3ebc8bb58033074f409b41c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comptr-class"></a>ComPtr – třída
Vytvoří *chytré ukazatele* typ, který reprezentuje rozhraní zadané parametr šablony. ComPtr automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, kdy přestane počet odkazů na nulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
class ComPtr;  
  
template<  
   class U  
>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Rozhraní zastupující ComPtr.  
  
 `U`  
 Třída, ke kterému je aktuální ComPtr přítel. (Šablony, která používá tento parametr je chráněn.)  
  
## <a name="remarks"></a>Poznámky  
 ComPtr <> deklaruje typ, který reprezentuje základní rozhraní ukazatele. Použít ComPtr <> deklarovat proměnnou a pak použijte operátor šipku přístup ke členu (`->`) pro přístup rozhraní – členská funkce.  
  
 Chytré ukazatele na další informace najdete v tématu "COM chytré ukazatele" dílčí části [postupy kódování COM](http://msdn.microsoft.com/en-us/76aca556-b4d6-4e67-a2a3-4439900f0c39)téma v knihovně MSDN.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`InterfaceType`|Synonymum pro v typu zadaném pomocí `T` parametr šablony.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Comptr::comptr – konstruktor](../windows/comptr-comptr-constructor.md)|Intializes novou instanci třídy ComPtr – třída. Přetížení zadejte výchozí, kopírovat, přesunout a převod konstruktory.|  
|[ComPtr:: ~ comptr – destruktor](../windows/comptr-tilde-comptr-destructor.md)|Deinitializes instanci ComPtr.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Comptr::AS – metoda](../windows/comptr-as-method.md)|Vrátí objekt ComPtr, který představuje rozhraní identifikovaný parametr určené šablony.|  
|[Comptr::asiid – metoda](../windows/comptr-asiid-method.md)|Vrátí objekt ComPtr, který představuje rozhraní identifikovaný ID specifikované rozhraní.|  
|[Comptr::asweak – metoda](../windows/comptr-asweak-method.md)|Načte slabé odkaz na aktuální objekt.|  
|[Comptr::Attach – metoda](../windows/comptr-attach-method.md)|Přidruží tento ComPtr určeného parametrem aktuální typ šablony typu rozhraní.|  
|[Comptr::CopyTo – metoda](../windows/comptr-copyto-method.md)|Zkopíruje zadané nebo aktuální rozhraní přidružené k této ComPtr na ukazatel zadaným výstupem.|  
|[Comptr::detach – metoda](../windows/comptr-detach-method.md)|Zrušíte tuto ComPtr z rozhraní, které představuje.|  
|[Comptr::Get – metoda](../windows/comptr-get-method.md)|Načte ukazatel na rozhraní, které souvisí s Tento ComPtr.|  
|[Comptr::getaddressof – metoda](../windows/comptr-getaddressof-method.md)|Načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datového člena, který obsahuje ukazatel na rozhraní reprezentována tento ComPtr.|  
|[Comptr::releaseandgetaddressof – metoda](../windows/comptr-releaseandgetaddressof-method.md)|Uvolní rozhraní přidružené k této ComPtr a pak načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datového člena, který obsahuje ukazatel na rozhraní, která byla vydána.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Uvolní všechny odkazy pro ukazatele na rozhraní, které souvisí s Tento ComPtr.|  
|[Comptr::swap – metoda](../windows/comptr-swap-method.md)|Rozhraní spravuje aktuální ComPtr s rozhraním spravuje zadaný ComPtr výměny.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Comptr::internaladdref – metoda](../windows/comptr-internaladdref-method.md)|Zvýší počet odkazů rozhraní přidružené k této ComPtr.|  
|[Comptr::internalrelease – metoda](../windows/comptr-internalrelease-method.md)|Provede operaci vydání COM v rozhraní přidružené k této ComPtr.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType operátor](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Určuje, zda ComPtr spravuje doba života objektu rozhraní.|  
|[ComPtr::operator & – operátor](../windows/comptr-operator-ampersand-operator.md)|Načte adresu aktuální ComPtr.|  
|[ComPtr::operator = – operátor](../windows/comptr-operator-assign-operator.md)|Přiřadí aktuální ComPtr hodnotu.|  
|[ComPtr::operator -> – operátor](../windows/comptr-operator-arrow-operator.md)|Načte ukazatel na typ určený parametrem aktuální šablony.|  
|[ComPtr::operator == – operátor](../windows/comptr-operator-equality-operator.md)|Určuje, zda dva objekty ComPtr jsou stejné.|  
|[ComPtr::operator! = – operátor](../windows/comptr-operator-inequality-operator.md)|Určuje, zda dva objekty ComPtr nejsou stejné.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Comptr::ptr_ – datový člen](../windows/comptr-ptr-data-member.md)|Obsahuje ukazatel na rozhraní, které je přidružené a spravuje tento ComPtr.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)