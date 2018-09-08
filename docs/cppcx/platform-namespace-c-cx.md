---
title: Platform – obor názvů (C + +/ CX) | Dokumentace Microsoftu
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb88b7b0d032ba5ff4e629279d61ad711ea42f4b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100454"
---
# <a name="platform-namespace-ccx"></a>Platform – obor názvů (C + +/ CX)

Obsahuje vestavěné typy, které jsou kompatibilní s modulem Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
using namespace Platform;
```

### <a name="members"></a>Členové

**Atributy**

Obor názvů Platform obsahuje atributy, tříd, výčtů, rozhraní a struktury. Platforma obsahuje také vnořené obory názvů.

|Atribut|Popis|
|---------------|-----------------|
|Příznaky|Označuje, že výčet lze považovat za bitové pole; To znamená, že sada příznaků.|
|MTAThread|Označuje, že model vláken pro aplikaci je vícevláknového objektu apartment (MTA).|
|STAThread|Označuje, že model vláken pro aplikaci je jednovláknový apartment (STA).|

**Třídy**

Obor názvů Platform má následující třídy.

|Třída|Popis|
|-----------|-----------------|
|[Platform::AccessDeniedException – třída](../cppcx/platform-accessdeniedexception-class.md)|Vyvoláno, když byl odepřen přístup k prostředku nebo funkce.|
|[Platform::Agile – třída](../cppcx/platform-agile-class.md)|Představuje objekt agilní jako objekt agile.|
|[Platform::Array – třída](../cppcx/platform-array-class.md)|Představuje upravitelné jednorozměrné pole.|
|[Platform::ArrayReference – třída](../cppcx/platform-arrayreference-class.md)|Představuje pole jejichž inicializace je optimalizována pro minimalizaci operací kopírování.|
|[Platform::Box – třída](../cppcx/platform-box-class.md)|Slouží k deklaraci zabalený typ, který zapouzdřuje hodnotu typu, jako jsou Windows::Foundation::DateTime nebo int64 typu je předána napříč binárním rozhraním aplikace (ABI) nebo uloží do proměnné typu [Platform::Object ^](../cppcx/platform-object-class.md).|
|[Platform::ChangedStateException – třída](../cppcx/platform-changedstateexception-class.md)|Vyvolána výjimka při volání metody iterátoru shromažďování nebo zobrazení kolekce po změně kolekce nadřazených, proto už není platná výsledky metody.|
|[Platform::ClassNotRegisteredException – třída](../cppcx/platform-classnotregisteredexception-class.md)|Vyvolána, když třída modelu COM není zaregistrovaný.|
|[Platform::COMException – třída](../cppcx/platform-comexception-class.md)|Představuje výjimku, která je vyvolána, pokud je vrácena nerozpoznaná hodnota z volání metody COM.|
|[Platform::Delegate – třída](../cppcx/platform-delegate-class.md)|Představuje podpis funkce zpětného volání.|
|[Platform::DisconnectedException – třída](../cppcx/platform-disconnectedexception-class.md)|Objekt se odpojil od svých klientů.|
|[Platform::Exception – třída](../cppcx/platform-exception-class.md)|Reprezentuje chyby, ke kterým dochází při spuštění aplikace. Základní třída pro výjimky.|
|[Platform::FailureException – třída](../cppcx/platform-failureexception-class.md)|Vyvolána, když operace se nezdařila. Jedná se o ekvivalent E_FAIL HRESULT.|
|[Platform::Guid – hodnotová třída](../cppcx/platform-guid-value-class.md)|Reprezentuje identifikátor GUID v systému typů modulu Windows Runtime.|
|[Platform::InvalidArgumentException – třída](../cppcx/platform-invalidargumentexception-class.md)|Vyvolána, když jeden z argumentů, poskytnutý metodě není platný.|
|[Platform::InvalidCastException – třída](../cppcx/platform-invalidcastexception-class.md)|Vyvolána v případě neplatné přetypování nebo explicitní převod.|
|[Platform::MTAThreadAttribute – třída](../cppcx/platform-mtathreadattribute-class.md)|Označuje, že model vláken pro aplikaci je vícevláknového objektu apartment (MTA).|
|[Platform::NotImplementedException – třída](../cppcx/platform-notimplementedexception-class.md)|Vyvolána, pokud se neimplementoval metodu rozhraní v třídě.|
|[Platform::NullReferenceException – třída](../cppcx/platform-nullreferenceexception-class.md)|Vyvolána, když je pokus přistoupit přes ukazatel odkaz na objekt s hodnotou null.|
|[Platform::Object – třída](../cppcx/platform-object-class.md)|Základní třída, která poskytuje společné chování.|
|[Platform::ObjectDisposedException – třída](../cppcx/platform-objectdisposedexception-class.md)|Vyvolána výjimka při provádění operace na smazaném objektu.|
|[Platform::OperationCanceledException – třída](../cppcx/platform-operationcanceledexception-class.md)|Vyvolána, pokud je operace přerušena.|
|[Platform::OutOfBoundsException – třída](../cppcx/platform-outofboundsexception-class.md)|Vyvolána, když se pokusí získat přístup k datům mimo platný rozsah operace.|
|[Platform::OutOfMemoryException – třída](../cppcx/platform-outofmemoryexception-class.md)|Vyvolána, když není dostatek paměti k dokončení operace.|
|[Platform::STAThreadAttribute – třída](../cppcx/platform-stathreadattribute-class.md)|Označuje, že model vláken pro aplikaci je jednovláknový apartment (STA).|
|[Platform::String – třída](../cppcx/platform-string-class.md)|Sekvenční kolekce znaků Unicode, který se používá k reprezentaci textu.|
|[Platform::StringReference – třída](../cppcx/platform-stringreference-class.md)|Umožňuje přístup k vyrovnávací paměti řetězců s minimální režie kopírování.|
|[Platform::Type – třída](../cppcx/platform-type-class.md)|Identifikuje předdefinovaný typ podle kategorie výčtu.|
|[Platform::ValueType – třída](../cppcx/platform-valuetype-class.md)|Základní třída pro instance typů hodnot.|
|[Platform::WeakReference – třída](../cppcx/platform-weakreference-class.md)|Poskytuje nestálý odkaz na objekty tříd ref, který se nezvyšuje počet odkazů.|
|[Platform::WriteOnlyArray – třída](../cppcx/platform-writeonlyarray-class.md)|Představuje jednorozměrné pole jen pro zápis sloužící jako vstupní parametr metody, které implementují vzor FillArray.|
|[Platform::WrongThreadException – třída](../cppcx/platform-wrongthreadexception-class.md)|Vyvolána, když vlákno volá prostřednictvím ukazatele rozhraní, které je objekt proxy serveru, který nepatří do objektu apartment vlákna.|

**Implementace rozhraní**

Obor názvů Platform definuje následující rozhraní.

|Rozhraní|Popis|
|---------------|-----------------|
|[Platform::IBox – rozhraní](../cppcx/platform-ibox-interface.md)|Sloužící k předávání typů hodnot na funkce, jejíž parametry jsou zadány jako Platform::Object ^.|
|[Platform::IBoxArray – rozhraní](../cppcx/platform-iboxarray-interface.md)|Rozhraní sloužící k předání do funkce, jejíž parametry jsou zadány jako Platform::Array pole typů hodnot.|
|[Platform::IDisposable – rozhraní](../cppcx/platform-idisposable-interface.md)|Používá se k uvolnění nespravovaných prostředků.|

**Výčty**

Obor názvů Platform má následující výčty.

|Rozhraní|Popis|
|---------------|-----------------|
|[Platform::CallbackContext – výčet](../cppcx/platform-callbackcontext-enumeration.md)|Výčet, který se používá jako parametr konstruktoru delegáta. Určuje, zda má být zařazeno do původní vlákna nebo volající vlákno zpětného volání.|
|[Platform::TypeCode – výčet](../cppcx/platform-typecode-enumeration.md)|Určuje číselný kategorii, která představuje předdefinovaný typ.|

**Struktury**

Obor názvů Platform má následující struktury.

|Struktura|Popis|
|---------------|-----------------|
|[Platform::Enum – třída](../cppcx/platform-enum-class.md)|Představuje pojmenované konstanty.|
|[Platform::Guid – hodnotová třída](../cppcx/platform-guid-value-class.md)|Reprezentuje identifikátor GUID.|
|[Platform::IntPtr – hodnotová třída](../cppcx/platform-intptr-value-class.md)|Podepsaný ukazatel, jehož velikost je vhodné pro platformu (32bitová nebo 64bitová verze).|
|[Platform::SizeT – hodnotová třída](../cppcx/platform-sizet-value-class.md)|Nepodepsaný datový typ, používá k reprezentování velikost objektu.|
|[Platform::UIntPtr – hodnotová třída](../cppcx/platform-uintptr-value-class.md)|Ukazatele bez znaménka jejíž velikost je vhodné pro platformu (32bitová nebo 64bitová verze).|

## <a name="see-also"></a>Viz také

[Platform::Collections – obor názvů](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Runtime::CompilerServices – obor názvů](../cppcx/platform-runtime-compilerservices-namespace.md)<br/>
[Platform::Runtime::InteropServices – obor názvů](../cppcx/platform-runtime-interopservices-namespace.md)<br/>
[Platform::Metadata – obor názvů](../cppcx/platform-metadata-namespace.md)