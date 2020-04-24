---
title: Dělení do vláken a zařazování (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 6b57366df5f466ffe49e4c0b46e05b1eed515535
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032483"
---
# <a name="threading-and-marshaling-ccx"></a>Dělení do vláken a zařazování (C++/CX)

V převážné většině případů instance tříd prostředí Windows Runtime, jako jsou standardní objekty jazyka C++, lze přistupovat z libovolného vlákna. Tyto třídy jsou označovány jako "agilní". Malý počet tříd prostředí Windows Runtime, které jsou dodávány se systémem Windows jsou však neagilní a musí být spotřebovány více jako objekty COM než standardní objekty C++. Nemusíte být odborníkem modelu COM k použití neagilních tříd, ale je třeba vzít v úvahu model zřetězení třídy a jeho chování zařazování. Tento článek obsahuje pozadí a pokyny pro ty vzácné scénáře, ve kterých je třeba využívat instanci třídy bez agilní.

## <a name="threading-model-and-marshaling-behavior"></a>Model zřetězení a chování zařazování

Třída Prostředí Windows Runtime může podporovat souběžný přístup podprocesu různými způsoby, jak je uvedeno dvěma atributy, které jsou na ni použity:

- `ThreadingModel`atribut může mít jednu z hodnot – STA, MTA `ThreadingModel` nebo Obojí, jak je definováno výčtu.

- `MarshallingBehavior`atribut může mít jednu z hodnot – Agilní, `MarshallingType` Žádný nebo Standardní, jak je definováno výčtu.

Atribut `ThreadingModel` určuje, kde je třída načtena při aktivaci: pouze v kontextu vlákna uživatelského rozhraní (STA), pouze v kontextu vlákna na pozadí (MTA) nebo v kontextu vlákna, které vytváří objekt (Oba). Hodnoty `MarshallingBehavior` atributů odkazují na to, jak se objekt chová v různých kontextech zřetězení; ve většině případů není třeba pochopit tyto hodnoty podrobně.  Z tříd, které jsou poskytovány rozhraní API systému Windows, o 90 procent mají `ThreadingModel`=Both a `MarshallingType`= Agile. To znamená, že mohou zpracovávat podrobnosti o podprocesech na nízké úrovni transparentně a efektivně.   Při použití `ref new` k vytvoření "agilní" třídy, můžete volat metody na něm z hlavního vlákna aplikace nebo z jednoho nebo více pracovních podprocesů.  Jinými slovy, můžete použít agilní třídu – bez ohledu na to, zda je poskytována systémem Windows nebo třetí stranou – z libovolného místa ve vašem kódu. Nemusíte se zabývat modelem podprocesu třídy nebo chováním zařazování.

## <a name="consuming-windows-runtime-components"></a>Náročné součásti prostředí Windows Runtime

Při vytváření aplikace univerzální platformy Windows můžete pracovat s agilními i neagilními součástmi. Při interakci s neagilní součásti, může dojít k následující upozornění.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Upozornění kompilátoru C4451 při využívání neagilních tříd

Z různých důvodů některé třídy nemůže být agilní. Pokud přistupujete k instancím neagilních tříd z vlákna uživatelského rozhraní i z vlákna na pozadí, věnujte zvláštní pozornost zajištění správného chování za běhu. Kompilátor Microsoft C++ vydává upozornění, když instanci neagilní run-time třídy ve vaší aplikaci v globálním oboru nebo deklarovat neagilní typ jako člen třídy v ref třídy, která sama je označena jako agilní.

Z neagilních tříd jsou nejjednodušší ty, které mají `ThreadingModel`=Both `MarshallingType`a =Standard.  Tyto třídy můžete agilní pouze `Agile<T>` pomocí pomocné třídy.   Následující příklad ukazuje deklaraci neagilní objekt `Windows::Security::Credentials::UI::CredentialPickerOptions^`typu a upozornění kompilátoru, který je vydán jako výsledek.

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

Zde je upozornění, které je vydáno:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Přidáte-li odkaz – na obor člena nebo globální obor – na objekt, který má zařazování chování "Standard", kompilátor vydá upozornění, které radí zabalit typ v `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Pokud používáte `Agile<T>`, můžete spotřebovat třídu, jako můžete jakékoli jiné agilní třídy. Použití `Platform::Agile<T>` za těchto okolností:

- Neagilní proměnná je deklarována v globálním oboru.

- Neagilní proměnná je deklarována v oboru třídy a je pravděpodobné, že spotřebovávající kód může propašovat ukazatel – to znamená použít v jiném apartment bez správného zařazování.

Pokud ani jedna z těchto podmínek platí, pak můžete označit obsahující třídy jako neagilní. Jinými slovy, měli byste přímo držet neagilní objekty pouze v neagilních třídách a držet\<neagilní objekty prostřednictvím platformy::Agile T> v agilních třídách.

Následující příklad ukazuje, `Agile<T>` jak používat, takže můžete bezpečně ignorovat upozornění.

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

Všimněte `Agile` si, že nelze předat jako vrácená hodnota nebo parametr ve třídě ref. Metoda `Agile<T>::Get()` vrátí popisovač na objekt (^), který můžete předat přes binární rozhraní aplikace (ABI) ve veřejné metodě nebo vlastnosti.

Při vytváření odkazu na in-proc Windows Runtime třídy, která má zařazování chování "None", kompilátor vydá `Platform::Agile<T>`upozornění C4451, ale nenavrhuje, že byste zvážit použití .  Kompilátor nemůže nabídnout žádnou pomoc kromě tohoto upozornění, takže je vaší odpovědností správně používat třídu a zajistit, aby váš kód volá součásti STA pouze z vlákna uživatelského rozhraní a součásti MTA pouze z vlákna na pozadí.

## <a name="authoring-agile-windows-runtime-components"></a>Vytváření agilních součástí prostředí Windows Runtime

Když definujete třídu ref v jazyce C++/CX, je ve výchozím `ThreadingModel`nastavení `MarshallingType`agilní – to znamená, že má =Both a =Agile.  Pokud používáte knihovnu šablon prostředí Windows Runtime C++, můžete třídu agilní odvozenou z aplikace `FtmBase`, která používá . `FreeThreadedMarshaller`  Pokud vytvoříte třídu, která má `ThreadingModel`=Both nebo `ThreadingModel`=MTA, ujistěte se, že třída je bezpečná pro přístup z více vláken.

Můžete upravit model zřetězení a zařazování chování ref třídy. Pokud však provedete změny, které vykreslují třídu bez agilní, musíte pochopit důsledky, které jsou spojeny s těmito změnami.

Následující příklad ukazuje, `MarshalingBehavior` jak `ThreadingModel` použít a atributy pro třídu runtime v knihovně třídy Prostředí Windows Runtime. Když aplikace používá knihovnu DLL a používá `ref new` klíčové slovo k aktivaci objektu `MySTAClass` třídy, objekt se aktivuje v jednovláknovém bytě a nepodporuje zařazování.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Nezapečetěné třídy musí mít zařazování a zřetězení nastavení atributů tak, aby kompilátor můžete ověřit, že odvozené třídy mají stejnou hodnotu pro tyto atributy. Pokud třída nemá nastavení nastavena explicitně, kompilátor generuje chybu a nepodaří se zkompilovat. Všechny třídy, která je odvozena z unsealedclass generuje chybu kompilátoru v jednom z těchto případů:

- `ThreadingModel` Atributy `MarshallingBehavior` a nejsou definovány v odvozené třídě.

- Hodnoty `ThreadingModel` atributy `MarshallingBehavior` a v odvozené třídě neodpovídají hodnotám v základní třídě.

Informace o podprocesu a zařazování, které je vyžadováno komponentou prostředí Windows Runtime jiného výrobce, jsou určeny v informacích o registraci manifestu aplikace pro komponentu. Doporučujeme, abyste všechny součásti prostředí Windows Runtime agilní. Tím zajistíte, že klientský kód může volat komponentu z libovolného vlákna v aplikaci a zlepšuje výkon těchto volání, protože se jedná o přímé volání, které nemají žádné zařazování. Pokud vytvoříte třídu tímto způsobem, pak kód `Platform::Agile<T>` klienta není třeba použít ke spotřebě třídy.

## <a name="see-also"></a>Viz také

[Model vláken](/uwp/api/windows.foundation.metadata.threadingmodel)<br/>
[MarshallingChování](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
