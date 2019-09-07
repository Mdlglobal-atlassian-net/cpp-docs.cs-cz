---
title: Dělení na vlákna a zařazováníC++(/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 05601367b6907e34d9d67364d35988a37ceae40c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741124"
---
# <a name="threading-and-marshaling-ccx"></a>Dělení na vlákna a zařazováníC++(/CX)

V obrovské většině případů jsou instance prostředí Windows Runtime třídy, jako jsou standardní C++ objekty, dostupné z libovolného vlákna. Takové třídy se označují jako "agilní". Nicméně malý počet prostředí Windows Runtime tříd, které jsou dodávány s Windows, je neagilní a musí se spotřebovat více jako objekty modelu COM než standardní C++ objekty. Nemusíte být odborníkem na model COM, abyste mohli používat neagilní třídy, ale je nutné vzít v úvahu model vláken třídy a jeho chování zařazování. Tento článek poskytuje základní informace a pokyny pro scénáře, ve kterých je nutné spotřebovat instanci neagilní třídy.

## <a name="threading-model-and-marshaling-behavior"></a>Model dělení na vlákna a chování zařazování

Prostředí Windows Runtime třída může podporovat souběžný přístup k vláknům různými způsoby, jak je uvedeno ve dvou atributech, které jsou na něj aplikovány:

- `ThreadingModel`atribut může mít jednu z hodnot – sta, MTA nebo obojí, jak je definováno `ThreadingModel` výčtem.

- `MarshallingBehavior`atribut může mít jednu z hodnot – agilní, žádný nebo standardní, jak je `MarshallingType` definováno výčtem.

`ThreadingModel` Atribut určuje, kde je třída načtena při aktivaci: pouze v kontextu vlákna uživatelského rozhraní (STA) pouze v kontextu vlákna na pozadí (MTA) nebo v kontextu vlákna, které vytváří objekt (obojí). Hodnoty `MarshallingBehavior` atributu odkazují na to, jak se objekt chová v různých kontextech zřetězení. ve většině případů nemusíte tyto hodnoty podrobněji porozumět.  Třídy, které jsou poskytovány rozhraním API systému Windows, přibližně 90% mají `ThreadingModel`= obojí a `MarshallingType`= agilní. To znamená, že mohou transparentně a efektivně zpracovávat podrobnosti o vláknech nízké úrovně.   Když použijete `ref new` k vytvoření agilní třídy, můžete na ni volat metody z hlavního vlákna aplikace nebo z jednoho nebo více pracovních vláken.  Jinými slovy, můžete použít agilní třídu – bez ohledu na to, zda je poskytována systémem Windows nebo třetí stranou – z libovolného místa v kódu. Nemusíte mít obavy z modelu vláken třídy nebo chování zařazování.

## <a name="consuming-windows-runtime-components"></a>Spotřebovávání komponent prostředí Windows Runtime

Když vytváříte aplikaci Univerzální platforma Windows, můžete pracovat s agilními i neagilními komponentami. Pokud pracujete s neagilními komponentami, může dojít k následujícímu upozornění.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Upozornění kompilátoru C4451 při spotřebovávání neagilních tříd

Z různých důvodů nemůžou být některé třídy agilní. Pokud přistupujete k instancím neagilních tříd jak z vlákna uživatelského rozhraní, tak z vlákna na pozadí, pak je potřeba mít další péči, abyste zajistili správné chování v době běhu. Při vytváření C++ instance neagilní běhové třídy ve vaší aplikaci v globálním oboru nebo deklarace neagilního typu jako člena třídy v referenční třídě, která je označena jako agilní, dojde k problémům s kompilátorem společnosti Microsoft.

Třídy, které nejsou agilní, nejjednodušší pro práci jsou ty, které mají `ThreadingModel`= obojí i `MarshallingType`= Standard.  Tyto třídy můžete zjednodušit pouhým použitím `Agile<T>` pomocné třídy.   Následující příklad ukazuje deklaraci neagilního objektu typu `Windows::Security::Credentials::UI::CredentialPickerOptions^`a upozornění kompilátoru, které je vystaveno v důsledku.

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

Tady je upozornění, které se vystavilo:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

Když přidáte odkaz – v oboru členů nebo globálním oboru – na objekt, který má chování zařazování "Standard", kompilátor vydá upozornění, které vás upozorní na zabalení typu v `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`Používáte-li `Agile<T>`, můžete třídu použít jako jakoukoli jinou agilní třídu. V `Platform::Agile<T>` těchto případech použijte:

- Neagilní proměnná je deklarována v globálním oboru.

- Neagilní proměnná je deklarována v oboru třídy a existuje možnost, že při využívání kódu může být ukazatel použit v jiném podmnožině bez správného zařazování.

Pokud neplatí žádná z těchto podmínek, můžete označit třídu, která ji obsahuje, jako neagilní. Jinými slovy, byste měli přímo držet neagilní objekty pouze v neagilních třídách a uchovávat neagilní objekty prostřednictvím Platform:: agilní\<T > v agilních třídách.

Následující příklad ukazuje, jak použít `Agile<T>` , abyste mohli upozornění bezpečně ignorovat.

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

Všimněte si `Agile` , že nelze předat jako návratovou hodnotu nebo parametr v referenční třídě. `Agile<T>::Get()` Metoda vrátí popisovač objektu (^), který můžete předat napříč binárním rozhraním aplikace (ABI) ve veřejné metodě nebo vlastnosti.

Když vytvoříte odkaz na prostředí Windows Runtime třídu, která má zařazování chování "none", kompilátor vydá upozornění C4451, ale nenavrhne použití `Platform::Agile<T>`.  Kompilátor nemůže nabízet žádnou nápovědu mimo toto upozornění, takže je vaše zodpovědnost za správné použití třídy a zajištění, že váš kód volá součásti STA pouze z vlákna uživatelského rozhraní a součásti MTA pouze z vlákna na pozadí.

## <a name="authoring-agile-windows-runtime-components"></a>Vytváření agilních prostředí Windows Runtime komponent

Pokud definujete referenční třídu v C++/CX, je ve výchozím nastavení agilní – to znamená, že má `ThreadingModel`hodnotu = obojí i `MarshallingType`= agilní.  Pokud používáte knihovnu šablon prostředí Windows Runtime C++ , můžete svou třídu agilním odvozovat odvozením z `FtmBase` `FreeThreadedMarshaller`, která používá.  Pokud vytváříte třídu, která má `ThreadingModel`= obojí nebo `ThreadingModel`= MTA, ujistěte se, že je třída bezpečná pro přístup z více vláken.

Můžete upravit model vláken a chování zařazování třídy ref class. Nicméně pokud provedete změny, které vykreslí třídu, která není agilní, je nutné pochopit důsledky, které jsou k těmto změnám přidruženy.

Následující příklad ukazuje, jak použít `MarshalingBehavior` a `ThreadingModel` atributy pro běhovou třídu v knihovně tříd prostředí Windows Runtime. Když aplikace používá knihovnu DLL a používá `ref new` klíčové slovo k `MySTAClass` aktivaci objektu třídy, je objekt aktivován v objektu apartment s jedním vláknem a nepodporuje zařazování.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Nezapečetěná třída musí mít nastavení atributů zařazování a vlákna, aby kompilátor mohl ověřit, že odvozené třídy mají stejnou hodnotu pro tyto atributy. Pokud třída nemá explicitně nastavené nastavení, kompilátor vygeneruje chybu a kompilace se nezdařila. Jakákoli třída odvozená z unsealedclass vygeneruje chybu kompilátoru v jednom z těchto případů:

- Atributy `ThreadingModel` a`MarshallingBehavior` nejsou definovány v odvozené třídě.

- Hodnoty atributů `ThreadingModel` a `MarshallingBehavior` v odvozené třídě se neshodují s hodnotami v základní třídě.

Informace o dělení na vlákna a zařazování, které vyžaduje součást prostředí Windows Runtime třetí strany, jsou uvedené v informacích o registraci manifestu aplikace pro komponentu. Doporučujeme, abyste všechny prostředí Windows Runtime komponenty byly agilní. Tím je zajištěno, že kód klienta může volat vaši komponentu z libovolného vlákna v aplikaci a zvyšuje výkon těchto volání, protože se jedná o Přímá volání, která nemají žádné zařazování. Pokud třídu vytváříte tímto způsobem, nemusí se kód klienta používat `Platform::Agile<T>` ke spotřebě vaší třídy.

## <a name="see-also"></a>Viz také:

[ThreadingModel](/uwp/api/Windows.Foundation.Metadata.ThreadingModel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
