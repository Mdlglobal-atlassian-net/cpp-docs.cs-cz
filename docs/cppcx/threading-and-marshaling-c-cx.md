---
title: Práce s vlákny a zařazování (C + +/ CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: faf541a0705de3e0e3d1b795d1abbdc2e9707974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582631"
---
# <a name="threading-and-marshaling-ccx"></a>Práce s vlákny a zařazování (C + +/ CX)

V převážné většině případů instance tříd modulu Windows Runtime, stejně jako se standardními objekty C++, je přístupný z libovolného vlákna. Tyto třídy jsou označovány jako "agilní". Ale malý počet Windows Runtime třídy, které se dodávají s Windows jsou mimo agilní a musí být využity více jako objekty modelu COM než standardní objektů jazyka C++. Nemusíte být odborníkem na modelu COM použít třídy – agile, ale potřeba vzít v úvahu třídy modelu vláken a její chování zařazování. Tento článek obsahuje základní informace a pokyny pro těchto výjimečných případech, ve kterých je nutné používat instanci-agilní třídy.

## <a name="threading-model-and-marshaling-behavior"></a>Model vláken a chování zařazování

Třída Windows Runtime podporuje přístupu souběžných vláken různými způsoby, je uvedené dva atributy, které se použijí k ní:

- `ThreadingModel` atribut může mít jednu z hodnot – STA, MTA, nebo obojí, podle definice `ThreadingModel` výčtu.

- `MarshallingBehavior` atribut může mít jednu z hodnot – Agile, None, nebo standardní podle definice `MarshallingType` výčtu.

`ThreadingModel` Atribut určuje, kde je načtena třída při aktivaci: jenom v kontextu (STA) vlákno uživatelského rozhraní, pouze v kontextu vlákna (MTA) na pozadí nebo v kontextu vlákna, která vytvoří objekt (i). `MarshallingBehavior` Hodnoty atributů odkazovat sama na chování na objekt v různých kontextech dělení na vlákna; ve většině případů není nutné pochopit tyto hodnoty podrobně.  Tříd, které jsou k dispozici v rozhraní Windows API, mají přibližně 90 procent `ThreadingModel`= obě a `MarshallingType`= Agile. To znamená, že se zpracování detailech dělení na vlákna transparentně a efektivně.   Při použití `ref new` vytvořit třídu "agilní", můžete volat metody v něm, z vaší hlavní aplikací vlákna nebo z jednoho nebo více pracovních vláken.  Jinými slovy, můžete použít třídu agilní – bez ohledu na to, zda je poskytnut Windows nebo třetí strany, z libovolného místa v kódu. Nemusíte mít obavy pomocí třídy model vláken nebo chování zařazování.

## <a name="consuming-windows-runtime-components"></a>Použití součástí prostředí Windows Runtime

Když vytvoříte aplikaci pro univerzální platformu Windows, může interaktivně pracovat s komponentami agilní a agile. Při interakci s-agilní komponenty, může dojít k následující upozornění.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Kompilátor varování C4451 při využívání-agilní třídy

Z různých důvodů nemůže být některé třídy agile. Pokud jste přístupu k instance-agilní tříd z vlákna uživatelského rozhraní a vlákna na pozadí, a pak provést další pro vás k zajištění správného chování za běhu. Kompilátor Visual C++ vyvolá upozornění při vytvoření instance – agile run-time třída ve vaší aplikaci v globálním oboru nebo deklarovat-agilní typ jako členem třídy ref class, která je označena jako agilní.

Agilní tříd nejjednodušší řešit jsou ty, které mají `ThreadingModel`= obě a `MarshallingType`= Standard.  Provedením těchto tříd agilní stačí použít `Agile<T>` pomocná třída.   Následující příklad ukazuje deklaraci-agilní objekt typu `Windows::Security::Credentials::UI::CredentialPickerOptions^`a upozornění kompilátoru, která je výsledkem vydala.

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

Toto je upozornění, která je vydala:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Když přidáte odkaz – člen oboru nebo globálním rozsahem – na objekt, který má chování zařazování "Standard", kompilátor vyvolá upozornění, s výzvou k zabalení typu v `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` používáte `Agile<T>`, můžete využívat třídy jako ostatní agilní třídy. Použití `Platform::Agile<T>` za těchto okolností:

- Agilní proměnná je deklarovaná v globálním oboru.

- Agilní proměnná je deklarovaná v oboru třídy a může se stát, že využívání kódu může smuggle ukazatel – to znamená, ho používat v různých objektu apartment bez správné zařazování.

Pokud ani jeden z těchto podmínek použití, můžete označit třídu obsahující jako agile. Jinými slovy, doporučujeme přímo držet-agilní objekty pouze v třídách agilní a držet objekty agilní prostřednictvím Platform::agile –\<T > v třídách agile.

Následující příklad ukazuje, jak používat `Agile<T>` tak, aby můžete upozornění ignorovat.

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

Všimněte si, že `Agile` nelze předat jako parametr ref class nebo návratovou hodnotu. `Agile<T>::Get()` Metoda vrátí popisovač na objektu (^), kterou můžete předat napříč binárním rozhraním aplikace (ABI) v veřejnou metodu nebo vlastnost.

V jazyce Visual C++, při vytváření odkazu na třídu prostředí Windows Runtime uvnitř procesu, který má chování zařazování "None", kompilátor vydá upozornění C4451 ale nebude navrhnout, zvažte použití `Platform::Agile<T>`.  Kompilátor nemůže nabízí pomoc nad rámec tohoto upozornění, proto je vaší odpovědností, abyste pomocí třídy správně a ujistěte se, že váš kód volá komponenty STA pouze z vlákna uživatelského rozhraní a komponenty MTA pouze z vlákna na pozadí.

## <a name="authoring-agile-windows-runtime-components"></a>Vytváření agilních součásti prostředí Windows Runtime

Při definování třídy ref class v jazyce C + +/ CX, je ve výchozím nastavení agilní – to znamená, že má `ThreadingModel`= obě a `MarshallingType`= Agile.  Pokud používáte knihovna šablon C++ Windows Runtime, můžete vytvořit třídu agilní odvozením z `FtmBase`, který používá `FreeThreadedMarshaller`.  Pokud vytváříte třídu, která má `ThreadingModel`= obě nebo `ThreadingModel`= MTA, ujistěte se, že třída je bezpečná pro vlákno.

Můžete upravit model vláken a zařazování chování třídy ref class. Pokud provedete změny, které vykreslují třídy bez agile, však musíte znát důsledky, které jsou spojeny s těmito změnami.

Následující příklad ukazuje, jak použít `MarshalingBehavior` a `ThreadingModel` atributy do třídy modulu runtime v knihovně tříd modulu Windows Runtime. Pokud aplikace používá knihovnu DLL a používá `ref new` – klíčové slovo k aktivaci `MySTAClass` třídu objektu, objekt se aktivuje v jednovláknovém objektu apartment a nepodporuje zařazování.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Nezapečetěné třídy musí mít atribut nastavení zařazování a dělení na vlákna, aby kompilátor můžete ověřit, že odvozené třídy mají stejnou hodnotu pro tyto atributy. Pokud třída nemá nastavené explicitně, kompilátor vygeneruje chybu a kompilace se nezdaří. Všechny třídy, která je odvozena z unsealedclass generuje chybu kompilátoru v některém z těchto případů:

- `ThreadingModel` a `MarshallingBehavior` atributů nejsou definovány v odvozené třídě.

- Hodnoty `ThreadingModel` a `MarshallingBehavior` atributy v odvozené třídě se neshodují v základní třídě.

Práce s vlákny a zařazovací informace, který vyžaduje prostředí Windows Runtime komponenty třetích stran je zadáno v manifestu registrační informace aplikace pro komponentu. Doporučujeme vám, abyste provedli všechny vaše součásti prostředí Windows Runtime agile. Tím se zajistí, že kód klienta můžete volat vaše komponenta z jakékoli vlákno v aplikaci a zlepšuje výkon při volání selžou, protože jsou přímá volání, které mají žádné zařazování. Pokud vytváříte vaší třídy tímto způsobem, pak klientský kód nebude muset používat `Platform::Agile<T>` využívat vaší třídy.

## <a name="see-also"></a>Viz také

[ThreadingModel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)<br/>
[MarshallingBehavior](https://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)