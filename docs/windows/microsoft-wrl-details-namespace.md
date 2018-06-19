---
title: 'Microsoft::WRL:: details – Namespace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a038509912c659cc820b73f16210ce874427112
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881767"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details – obor názvů
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Microsoft::WRL::Details;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRef – třída](../windows/comptrref-class.md)|Představuje odkaz na objekt typu ComPtr\<T >.|  
|[ComPtrRefBase – třída](../windows/comptrrefbase-class.md)|Představuje základní třídu pro [ComPtrRef](../windows/comptrref-class.md) třídy.|  
|[DontUseNewUseMake – třída](../windows/dontusenewusemake-class.md)|Zabraňuje pomocí operátoru `new` v `RuntimeClass`. V důsledku toho je nutné použít [Make – funkce](../windows/make-function.md) místo.|  
|[EventTargetArray – třída](../windows/eventtargetarray-class.md)|Představuje pole obslužné rutiny událostí.|  
|[MakeAllocator – třída](../windows/makeallocator-class.md)|Pro třídu activatable s nebo bez podpory slabé odkaz přidělí paměť.|  
|[ModuleBase – třída](../windows/modulebase-class.md)|Představuje základní třídu [modulu](../windows/module-class.md) třídy.|  
|[RemoveIUnknown – třída](../windows/removeiunknown-class.md)|Vytvoří typ, který je ekvivalentní `IUnknown`-založené na typ, ale má nevirtuálních `QueryInterface`, `AddRef`, a `Release` metody.|  
|[WeakReference – třída](../windows/weakreference-class1.md)|Představuje *slabé odkaz* , lze pomocí prostředí Windows Runtime nebo klasického modelu COM. Slabé odkazy představuje objekt, který může nebo nemusí být dostupné.|  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[ArgTraits – struktura](../windows/argtraits-structure.md)|Deklaruje zadaného delegáta rozhraní a anonymní – členská funkce, který má zadaný počet parametrů.|  
|[ArgTraitsHelper – struktura](../windows/argtraitshelper-structure.md)|Pomáhá definovat běžné vlastnosti delegáta argumenty.|  
|[BoolStruct – struktura](../windows/boolstruct-structure.md)|Definuje, zda je ComPtr správou doba života objektu rozhraní. Boolstruct – se používá interně pomocí [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operátor.|  
|[CreatorMap – struktura](../windows/creatormap-structure.md)|Obsahuje informace o tom, jak inicializovat, zaregistrujte a zrušit registraci objekty.|  
|[DerefHelper – struktura](../windows/derefhelper-structure.md)|Představují dereferenced ukazatel `T*` parametr šablony.|  
|[EnableIf – struktura](../windows/enableif-structure.md)|Definuje členem data v typu zadaném pomocí druhý parametr šablony, pokud je první parametr šablony výsledkem `true`.|  
|[FactoryCache – struktura](../windows/factorycache-structure.md)|Obsahuje umístění objekt pro vytváření tříd a hodnotu, která identifikuje registrované objektu třídy prostředí Windows Runtime nebo COM.|  
|[ImplementsBase – struktura](../windows/implementsbase-structure.md)|Slouží k ověření typy parametrů šablony v [implementuje strukturu](../windows/implements-structure.md).|  
|[ImplementsHelper – struktura](../windows/implementshelper-structure.md)|Pomáhá implementovat [implementuje](../windows/implements-structure.md) struktura.|  
|[InterfaceList – struktura](../windows/interfacelist-structure.md)|Umožňuje vytvořit seznam rekurzivní rozhraní.|  
|[InterfaceListHelper – struktura](../windows/interfacelisthelper-structure.md)|Sestavení `InterfaceList` typu podle rekurzivně použití argumenty parametrů určené šablony.|  
|[InterfaceTraits – struktura](../windows/interfacetraits-structure.md)|Implementuje běžné vlastnosti rozhraní.|  
|[InvokeHelper – struktura](../windows/invokehelper-structure.md)|Poskytuje implementaci Invoke metody založené na zadaný počet a typ argumentů.|  
|[IsBaseOfStrict – struktura](../windows/isbaseofstrict-structure.md)|Ověřuje, zda je jeden typ základní jiného.|  
|[IsSame – struktura](../windows/issame-structure.md)|Testy, zda jeden zadaný typ je stejná jako jiné zadaný typ.|  
|[Nil – struktura](../windows/nil-structure.md)|Slouží k určení parametru šablony neurčené, volitelné.|  
|[RemoveReference – struktura](../windows/removereference-structure.md)|Odstraní odkaz nebo deklarátor odkazu znak z parametru šablony zadanou třídu.|  
|[RuntimeClassBase – struktura](../windows/runtimeclassbase-structure.md)|Slouží k detekci `RuntimeClass` v [zkontrolujte](../windows/make-function.md) funkce.|  
|[RuntimeClassBaseT – struktura](../windows/runtimeclassbaset-structure.md)|Poskytuje pomocné metody pro `QueryInterface` operace a získávání ID rozhraní.|  
|[VerifyInheritanceHelper – struktura](../windows/verifyinheritancehelper-structure.md)|Ověřuje, zda jedno rozhraní je odvozený od jiného rozhraní.|  
|[VerifyInterfaceHelper – struktura](../windows/verifyinterfacehelper-structure.md)|Ověří, že rozhraní zadané parametr šablony splňuje určité požadavky.|  
  
### <a name="enumerations"></a>Výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncStatusInternal – výčet](../windows/asyncstatusinternal-enumeration.md)|Určuje mapování mezi interní výčty pro stav asynchronní operace a **Windows::Foundation::AsyncStatus** výčtu.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[ActivationFactoryCallback – funkce](../windows/activationfactorycallback-function.md)|Získá objekt factory aktivace pro ID zadaná aktivace.|  
|[Move – funkce](../windows/move-function.md)|Přesune zadaného argumentu z jednoho umístění do druhého.|  
|[RaiseException – funkce](../windows/raiseexception-function.md)|Vyvolá výjimku v volající vlákno.|  
|[Swap – funkce (knihovna šablon C++ prostředí Windows Runtime)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Výměny hodnoty dvou zadaných argumentů.|  
|[TerminateMap – funkce](../windows/terminatemap-function.md)|Vypne tříd v zadaný modul.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)