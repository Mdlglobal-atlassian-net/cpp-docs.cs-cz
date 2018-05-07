---
title: Obor názvů Platform (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- Platform/Platform
dev_langs:
- C++
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 348bedcde953cbcd6084023d6f7117c7f7f001f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platform-namespace-ccx"></a>Obor názvů Platform (C + +/ CX)
Obsahuje vestavěné typy, které jsou kompatibilní s prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
using namespace Platform;  
```  
  
### <a name="members"></a>Členové  
 **Atributy**  
  
 Obor názvů Platform obsahuje atributy a třídy, výčty, rozhraní a struktury. Platforma obsahuje také vnořené obory názvů.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Příznaky|Určuje, zda výčet lze považovat za pole bit; To znamená, sadu příznaků.|  
|MTAThread|Označuje, že je modelu vláken pro aplikace Vícevláknová apartment (MTA).|  
|STAThread|Označuje, že modelu vláken pro aplikaci je single-threaded apartment (STA).|  
  
 **Třídy**  
  
 Obor názvů Platform má následující třídy.  
  
|Třída|Popis|  
|-----------|-----------------|  
|[Platform::AccessDeniedException – třída](../cppcx/platform-accessdeniedexception-class.md)|Vyvolá, když byl odepřen přístup k prostředku nebo funkce.|  
|[Platform::Agile – třída](../cppcx/platform-agile-class.md)|Představuje objekt agilní jako agile objekt.|  
|[Platform::Array – třída](../cppcx/platform-array-class.md)|Představuje jednorozměrné, upravitelnými pole.|  
|[Platform::ArrayReference – třída](../cppcx/platform-arrayreference-class.md)|Představuje pole jehož inicializace je optimalizovaná tak, aby minimalizovat operací kopírování.|  
|[Platform::Box – třída](../cppcx/platform-box-class.md)|Používá k deklaraci zabalený typ, který zapouzdřuje typ hodnoty, jako je například Windows::Foundation::DateTime nebo int64, když tento typ je předán přes rozhraní binární aplikace (ABI) nebo uložené v proměnné typu [Platform::Object ^](../cppcx/platform-object-class.md).|  
|[Platform::ChangedStateException – třída](../cppcx/platform-changedstateexception-class.md)|Vyvolá, když jsou volány metody iterator kolekce nebo kolekce zobrazení po změně její nadřazená kolekce, zneplatnění výsledky metody.|  
|[Platform::ClassNotRegisteredException – třída](../cppcx/platform-classnotregisteredexception-class.md)|Vyvolá, když třídy COM není zaregistrován.|  
|[Platform::COMException – třída](../cppcx/platform-comexception-class.md)|Představuje výjimku, která se vyvolá, když je vrácena nerozpoznané hodnota z volání metody COM.|  
|[Platform::Delegate – třída](../cppcx/platform-delegate-class.md)|Představuje podpis funkce zpětného volání.|  
|[Platform::DisconnectedException – třída](../cppcx/platform-disconnectedexception-class.md)|Objekt byl odpojen od svých klientů.|  
|[Platform::Exception – třída](../cppcx/platform-exception-class.md)|Reprezentuje chyby, ke kterým došlo během provádění aplikací. Základní třída pro výjimky.|  
|[Platform::FailureException – třída](../cppcx/platform-failureexception-class.md)|Vyvolá, když operace se nezdařila. Jde o ekvivalent E_FAIL HRESULT.|  
|[Platform::Guid – hodnotová třída](../cppcx/platform-guid-value-class.md)|Představuje identifikátor GUID v prostředí Windows Runtime typ systému.|  
|[Platform::InvalidArgumentException – třída](../cppcx/platform-invalidargumentexception-class.md)|Vyvolá, když jeden z argumentů poskytnutý metodě je neplatný.|  
|[Platform::InvalidCastException – třída](../cppcx/platform-invalidcastexception-class.md)|Vyvolána v případě neplatné přetypování nebo explicitní převod.|  
|[Platform::MTAThreadAttribute – třída](../cppcx/platform-mtathreadattribute-class.md)|Označuje, že je modelu vláken pro aplikace Vícevláknová apartment (MTA).|  
|[Platform::NotImplementedException – třída](../cppcx/platform-notimplementedexception-class.md)|Vygeneruje se, pokud nebyla implementována ve třídě metodu rozhraní.|  
|[Platform::NullReferenceException – třída](../cppcx/platform-nullreferenceexception-class.md)|Vygeneruje se při pokusu o dereference odkaz objektu null.|  
|[Platform::Object – třída](../cppcx/platform-object-class.md)|Základní třída, která poskytuje společné chování.|  
|[Platform::ObjectDisposedException – třída](../cppcx/platform-objectdisposedexception-class.md)|Vygeneruje se při provádění operace v uvolněné objektu.|  
|[Platform::OperationCanceledException – třída](../cppcx/platform-operationcanceledexception-class.md)|Vyvolá, když operace byla přerušena.|  
|[Platform::OutOfBoundsException – třída](../cppcx/platform-outofboundsexception-class.md)|Vygeneruje se, když se operace pokusí o přístup k datům mimo platný rozsah.|  
|[Platform::OutOfMemoryException – třída](../cppcx/platform-outofmemoryexception-class.md)|Vyvolá, když není dostatek paměti pro dokončení operace.|  
|[Platform::STAThreadAttribute – třída](../cppcx/platform-stathreadattribute-class.md)|Označuje, že modelu vláken pro aplikaci je single-threaded apartment (STA).|  
|[Platform::String – třída](../cppcx/platform-string-class.md)|Sekvenční kolekce znaky znakové sady Unicode, která se používá k reprezentování text.|  
|[Platform::StringReference – třída](../cppcx/platform-stringreference-class.md)|Umožňuje přístup do řetězce vyrovnávacích pamětí s minimální režie kopie.|  
|[Platform::Type – třída](../cppcx/platform-type-class.md)|Identifikuje předdefinovaný typ výčtem kategorie.|  
|[Platform::ValueType – třída](../cppcx/platform-valuetype-class.md)|Základní třída pro typy hodnot instancí.|  
|[Platform::WeakReference – třída](../cppcx/platform-weakreference-class.md)|Poskytuje slabé odkaz na objekty tříd ref, který se nezvyšuje počet odkazů.|  
|[Platform::WriteOnlyArray – třída](../cppcx/platform-writeonlyarray-class.md)|Představuje jednorozměrné pole jen pro zápis, který se používá jako vstupní parametr pro metody, které implementují FillArray vzor.|  
|[Platform::WrongThreadException – třída](../cppcx/platform-wrongthreadexception-class.md)|Vyvolá, když vlákno volá prostřednictvím ukazatele rozhraní, což je pro objekt proxy serveru, který nepatří do objektu apartment vlákna.|  
  
 **Implementace rozhraní**  
  
 Obor názvů Platform definuje následující rozhraní.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[Platform::IBox – rozhraní](../cppcx/platform-ibox-interface.md)|Sloužící k předávání typů hodnot na funkce, jejíž parametry jsou zadány jako Platform::Object ^.|  
|[Platform::IBoxArray – rozhraní](../cppcx/platform-iboxarray-interface.md)|Rozhraní sloužící k předávání pole typů hodnot na funkce, jejíž parametry jsou zadány jako Platform::Array.|  
|[Platform::IDisposable – rozhraní](../cppcx/platform-idisposable-interface.md)|Použít k uvolnění nespravovaných prostředků.|  
  
 **Výčty**  
  
 Obor názvů Platform má následující výčty.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[Platform::CallbackContext – výčet](../cppcx/platform-callbackcontext-enumeration.md)|Výčet, který se používá jako parametr funkce konstruktor delegáta. Určuje, zda má být zařazeno do původní vlákna nebo volající vlákno zpětné volání.|  
|[Platform::TypeCode – výčet](../cppcx/platform-typecode-enumeration.md)|Určuje číselnou kategorii, která představuje předdefinovaný typ.|  
  
 **Struktury**  
  
 Obor názvů Platform má následující struktury.  
  
|Struktura|Popis|  
|---------------|-----------------|  
|[Platform::Enum – třída](../cppcx/platform-enum-class.md)|Představuje pojmenovanou konstanta.|  
|[Platform::Guid – hodnotová třída](../cppcx/platform-guid-value-class.md)|Představuje identifikátor GUID.|  
|[Platform::IntPtr – hodnotová třída](../cppcx/platform-intptr-value-class.md)|Podepsaný ukazatel jejíž aktuální velikost je vhodný pro platformu (32bitová nebo 64bitová verze).|  
|[Platform::SizeT – hodnotová třída](../cppcx/platform-sizet-value-class.md)|Typ nepodepsaná data používá k reprezentování velikost objektu.|  
|[Platform::UIntPtr – hodnotová třída](../cppcx/platform-uintptr-value-class.md)|Nepodepsané ukazatel, jejíž aktuální velikost je vhodný pro platformu (32bitová nebo 64bitová verze).|  
  
## <a name="see-also"></a>Viz také  
 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Namespace Platform::Runtime::CompilerServices](../cppcx/platform-runtime-compilerservices-namespace.md)   
 [Namespace Platform::Runtime::InteropServices](../cppcx/platform-runtime-interopservices-namespace.md)   
 [Platform::Metadata – obor názvů](../cppcx/platform-metadata-namespace.md)