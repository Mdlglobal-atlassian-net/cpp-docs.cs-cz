---
title: "Dělení na vlákna a zařazování (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1544f18d0d5206e178cf42705d9567fad2423c
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2018
---
# <a name="threading-and-marshaling-ccx"></a>Dělení na vlákna a zařazování (C + +/ CX)
V valná většina případů instance tříd prostředí Windows Runtime, jako je standardními objekty C++ je přístupná z libovolného vlákna. Tyto třídy jsou označovány jako "agile". Ale malý počet prostředí Windows Runtime třídy, dodávané se systémem Windows jsou bez agilní a musí být využívány více jako objektů COM než standardními objekty C++. Nemusíte být COM expert používat-agilní třídy, ale nutné vzít v úvahu třídy modelu vláken a její chování zařazování. Tento článek obsahuje základní informace a pokyny pro tyto výjimečných scénářů, ve kterých budete muset používat instanci-agilní třídy.  
  
## <a name="threading-model-and-marshaling-behavior"></a>Model vláken a chování zařazování  
 Prostředí Windows Runtime třídy může podporovat souběžných vláken přístup různými způsoby, jak dva atributy, které se použijí k němu:  
  
-   `ThreadingModel` atribut může mít jednu z hodnot – STA, MTA, nebo obojí, podle definice `ThreadingModel` výčtu.  
  
-   `MarshallingBehavior` atribut může mít jednu z hodnot – agilní, None, nebo Standard podle definice `MarshallingType` výčtu.  
  
 `ThreadingModel` Atribut určuje, kde je třída načtena při aktivaci: pouze v kontextu vláken (STA) uživatelského rozhraní, pouze v kontextu vláken (MTA) pozadí nebo v kontextu vlákna, který vytvoří objekt (oba). `MarshallingBehavior` Hodnoty atributu odkazovat na chování objektu v různých kontextech vláken; ve většině případů nemusíte pochopit tyto hodnoty podrobně.  Třídy, které jsou k dispozici rozhraním API systému Windows, o 90 procent mít `ThreadingModel`= obě a `MarshallingType`= Agile. To znamená, že jejich zpracovat detailech vláken transparentně a efektivně.   Při použití `ref new` vytvořit třídu "agile", nebo můžete volat metody na něm z vlákna vaší hlavní aplikace z jednoho nebo více pracovních vláken.  Jinými slovy, můžete použít třídu agilní – bez ohledu na to, jestli je poskytnut Windows nebo třetí strany – z libovolného místa v kódu. Nemusíte dělat starosti s třídu model vláken nebo chování zařazování.  
  
## <a name="consuming-windows-runtime-components"></a>Spotřeba součástí prostředí Windows Runtime  
 Když vytvoříte aplikaci pro univerzální platformu Windows, může komunikovat s agile a agilní součásti. Pokud při práci s-agilní součásti, můžete setkat s následujícím upozorněním.  
  
### <a name="compiler-warning-when-consuming-non-agile-classes-c4451"></a>Upozornění kompilátoru při využívání-agilní třídy (C4451)  
 Z různých důvodů nemůže být agilní některé třídy. Pokud instance tříd agilní přistupují z vlákna uživatelského rozhraní a vlákna na pozadí, můžete provést další péči, aby zajistila správné chování za běhu. Kompilátor Visual C++ vydá upozornění při vytváření instancí-agilní run-time třída ve vaší aplikaci v globálním oboru nebo deklarovat-agilní typ jako člena třídy v ref třída, která sama je označen jako agile.  
  
 Agilní třídy nejjednodušší řešení jsou ty, které mají `ThreadingModel`= obě a `MarshallingType`= Standard.  Můžete provést tyto třídy agilní jenom pomocí `Agile<T>` pomocná třída.   Následující příklad ukazuje deklaraci-agilní objektu typu `Windows::Security::Credentials::UI::CredentialPickerOptions^`a upozornění kompilátoru, který je výsledkem je vydán.  
  
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
  
 Když přidáte odkaz – v oboru člen nebo globálním rozsahem – na objekt, který má zařazování chování "Standard", vydá upozornění s výzvou k zabalení typu v `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Pokud používáte `Agile<T>`, můžete využívat třídy Například můžete jiná agilní třída. Použití `Platform::Agile<T>` za těchto okolností:  
  
-   Agilní proměnné je deklarován v globálním oboru.  
  
-   Agilní proměnné je deklarován v rozsah třídy a existuje pravděpodobnost, využívání kódu může smuggle ukazatele – to znamená, používají v různých apartment bez správné zařazování.  
  
 Pokud ani jedno z těchto podmínek použití, můžete označit obsahující třídu jako agile. Jinými slovy, doporučujeme přímo jenom v jiných agilní třídy obsahovat-agilní objekty a uložení-agilní objekty prostřednictvím Platform::Agile\<T > v agilní třídy.  
  
 Následující příklad ukazuje, jak používat `Agile<T>` tak, aby můžete bezpečně ignorovat upozornění.  
  
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
  
 Všimněte si, že `Agile` nelze předat jako návratová hodnota nebo parametr v třídě ref. `Agile<T>::Get()` Metoda vrací popisovač na objekt (^), které můžete předat napříč binární rozhraní aplikace (ABI) ve veřejné metody nebo vlastnosti.  
  
 V jazyce Visual C++, při vytváření odkaz na prostředí Windows Runtime třídy vnitřním, která má chování zařazování "Žádný", kompilátor vydá upozornění C4451, ale nemá navrhovat, zvažte použití `Platform::Agile<T>`.  Kompilátor nelze nabízejí pomoc nad rámec tohoto upozornění, takže je vaší povinností použití třídy správně a ujistěte se, že váš kód volá STA pouze z vlákna uživatelského rozhraní a komponenty modelu MTA pouze z vlákna na pozadí.  
  
## <a name="authoring-agile-windows-runtime-components"></a>Agilní prostředí Windows Runtime součásti pro vytváření obsahu  
 Když definujete třídu ref v jazyce C + +/ CX, je ve výchozím nastavení agilní – to znamená, má `ThreadingModel`= obě a `MarshallingType`= Agile.  Pokud používáte [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)], můžete použít třídu agilní odvozené z `FtmBase`, které používá `FreeThreadedMarshaller`.  Pokud vytváříte třídu, která má `ThreadingModel`= obě nebo `ThreadingModel`= MTA, ujistěte se, že třída je bezpečné pro přístup z více vláken. Další informace najdete v tématu [vytvořit a používat objekty (WRL)](http://msdn.microsoft.com/en-us/d5e42216-e888-4f1f-865a-b5ccd0def73e).  
  
 Model vláken a chování zařazování ref třídy můžete upravit. Pokud provedete změny, které vykreslení bez agilní třída, však musíte pochopit důsledky, které jsou spojeny s těmito změnami.  
  
 Následující příklad ukazuje, jak se má použít `MarshalingBehavior` a `ThreadingModel` atributy na třídu runtime v prostředí Windows Runtime knihovny tříd. Pokud aplikace používá knihovnu DLL a používá `ref new` – klíčové slovo k aktivaci `MySTAClass` třídu objektu, objekt za single-threaded apartment se aktivuje a nepodporuje kódování.  
  
```  
using namespace Windows::Foundation::Metadata;  
using namespace Platform;  
  
[Threading(ThreadingModel::STA)]  
[MarshalingBehavior(MarshalingType::None)]   
public ref class MySTAClass  
{  
};  
  
```  
 
 Třídu nezapečetěné musí mít zařazování a vláken nastavení atributů tak, aby kompilátor můžete ověřit, že odvozené třídy mají stejnou hodnotu pro tyto atributy. Pokud třída nemá nastavení explicitně nastaven, kompilátor vygeneruje chybu a se nepovede zkompilovat. Všechny třídy, která je odvozena z unsealedclass generuje chybu kompilátoru v některém z těchto případech:  
  
-   `ThreadingModel` a `MarshallingBehavior` atributy nejsou definovány v odvozené třídě.  
  
-   Hodnoty `ThreadingModel` a `MarshallingBehavior` atributy v odvozené třídě neodpovídají hodnotám v základní třídě.  
  
 Dělení na vlákna a zařazování informace, které je požadované pro prostředí Windows Runtime součást jiného výrobce je zadáno v manifestu registrační informace aplikace pro komponentu. Doporučujeme, abyste vytvořili všechny součásti prostředí Windows Runtime agilní. To zajišťuje, že kód klienta můžete volat příslušné součásti z jakékoli vlákno v aplikaci a zvyšuje výkon těchto volání, protože jsou přímá volání, které mají žádné zařazování. Pokud vytváříte třídě tímto způsobem, pak kód klienta nemá používat `Platform::Agile<T>` používat vlastní třídy.  
  
## <a name="see-also"></a>Viz také  
 [ThreadingModel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)   
 [MarshallingBehavior](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)