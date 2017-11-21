---
title: Microsoft::WRL Namespace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
dev_langs: C++
helpviewer_keywords: WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7b3c3bef713bd63b7b82761ce36ab039556e63c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL – obor názvů
Definuje základní typy, které tvoří knihovna šablon C++ Runtime systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Microsoft::WRL;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="typedefs"></a>Typedefs  
  
|Název|Popis|  
|----------|-----------------|  
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[ActivationFactory – třída](../windows/activationfactory-class.md)|Umožňuje jednu nebo více tříd, které chcete aktivovat pomocí prostředí Windows Runtime.|  
|[AsyncBase – třída](../windows/asyncbase-class.md)|Implementuje počítač asynchronní stavu prostředí Windows Runtime.|  
|[ClassFactory – třída](../windows/classfactory-class.md)|Implementuje základních funkcí `IClassFactory` rozhraní.|  
|[ComPtr – třída](../windows/comptr-class.md)|Vytvoří *chytré ukazatele* typ, který reprezentuje rozhraní zadané parametr šablony. ComPtr automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, kdy přestane počet odkazů na nulu.|  
|[DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md)|Třída Šablona používaná pro typy argumentů událostí pro rozlišených položek.|  
|[EventSource – třída](../windows/eventsource-class.md)|Představuje událost. `EventSource`Členské funkce přidání, odebrání a vyvolání obslužné rutiny událostí.|  
|[FtmBase – třída](../windows/ftmbase-class.md)|Představuje objekt volné zařazování vláken.|  
|[Module – třídy](../windows/module-class.md)|Představuje kolekci související objekty.|  
|[RuntimeClass – třída](../windows/runtimeclass-class.md)|Představuje instancí třídu, která dědí zadaný počet rozhraní a obsahuje zadané prostředí Windows Runtime, classic COM a slabé odkaz na podporu.|  
|[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)|Poskytuje základní mechanismus pro vytvoření klasického základní třídy COM nebo prostředí Windows Runtime.|  
|[SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)|Poskytuje základní mechanismus pro vytvoření základní třídy.|  
|[WeakRef – třída](../windows/weakref-class.md)|Představuje *slabé odkaz* které lze použít pouze prostředí Windows Runtime, není klasického modelu COM. Slabé odkazy představuje objekt, který může nebo nemusí být dostupné.|  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[Chaininterfaces – struktura](../windows/chaininterfaces-structure.md)|Určuje ověření a Inicializace funkce, které mohou být použity pro sadu rozhraní ID.|  
|[Cloakediid – struktura](../windows/cloakediid-structure.md)|Šablon RuntimeClass, implementuje a chaininterfaces – označuje, že zadané rozhraní není dostupný v seznamu IID.|  
|[Implements – struktura](../windows/implements-structure.md)|Implementuje QueryInterface a GetIid pro zadaná rozhraní.|  
|[MixIn – struktura](../windows/mixin-structure.md)|Zajišťuje třídu runtime, pochází z prostředí Windows Runtime rozhraní, pokud existuje a pak classic COM – rozhraní.|  
|[Runtimeclassflags – struktura](../windows/runtimeclassflags-structure.md)|Obsahuje typu pro instanci [RuntimeClass](../windows/runtimeclass-class.md).|  
  
### <a name="enumerations"></a>Výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncResultType – výčet](../windows/asyncresulttype-enumeration.md)|Určuje typ výsledku vrácený metodou GetResults().|  
|[ModuleType – výčet](../windows/moduletype-enumeration.md)|Určuje, zda modul musí podporovat proces serveru nebo serveru mimo proces.|  
|[RuntimeClassType – výčet](../windows/runtimeclasstype-enumeration.md)|Určuje typ [RuntimeClass](../windows/runtimeclass-class.md) instance, která je podporována.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[Asweak – funkce](../windows/asweak-function.md)|Načte slabé odkaz na zadané instanci.|  
|[Funkce zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md)|Vytvoří objekt, jehož členská funkce je metoda zpětného volání.|  
|[Createactivationfactory – funkce](../windows/createactivationfactory-function.md)|Vytvoří objekt factory, který vytváří instance pro zadanou třídu, která může být aktivovaný pomocí prostředí Windows Runtime.|  
|[Createclassfactory – funkce](../windows/createclassfactory-function.md)|Vytvoří objekt factory, který vytváří instance pro zadanou třídu.|  
|[Make – funkce](../windows/make-function.md)|Inicializuje pro zadanou třídu prostředí Windows Runtime.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: wrappers – Namespace](../windows/microsoft-wrl-wrappers-namespace.md)