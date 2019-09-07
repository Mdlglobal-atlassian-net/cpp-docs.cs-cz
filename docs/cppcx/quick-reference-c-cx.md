---
title: Rychlý odkaz (C++/CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: 2826105f7ec4a680208965fcc18a548c6ec4b795
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740921"
---
# <a name="quick-reference-ccx"></a>Rychlý odkaz (C++/CX)

Prostředí Windows Runtime podporuje aplikace Univerzální platforma Windows (UWP), které se spouštějí pouze v důvěryhodném prostředí operačního systému, používají autorizované funkce, datové typy a zařízení a jsou distribuovány prostřednictvím Microsoft Store. C++/CX zjednodušuje psaní aplikací pro prostředí Windows Runtime. Tento článek je rychlým odkazem. Podrobnější dokumentaci najdete v tématu [Typ systému](../cppcx/type-system-c-cx.md).

Při sestavování na příkazovém řádku použijte možnost kompilátoru **/ZW** k vytvoření aplikace UWP nebo součásti prostředí Windows Runtime. Chcete-li získat přístup k deklaracím prostředí Windows Runtime, které jsou definovány v souborech prostředí Windows Runtime metadata (. winmd `#using` ), zadejte direktivu nebo možnost kompilátoru **/Fu** . Když vytvoříte projekt pro aplikaci UWP, sada Visual Studio ve výchozím nastavení nastaví tyto možnosti a přidá odkazy na všechny knihovny prostředí Windows Runtime.

## <a name="quick-reference"></a>Stručná referenční dokumentace

|Koncept|Standardní C++|C++/CX|Poznámky|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|Základní typy|C++základní typy.|C++/CX – základní typy, které implementují základní typy, které jsou definovány v prostředí Windows Runtime.|Obor názvů obsahuje C++integrované základní typy pro/CX. `default` Kompilátor implicitně mapuje C++základní typy/CX na standardní C++ typy.<br /><br /> `Platform` Rodina oborů názvů obsahuje typy, které implementují základní prostředí Windows Runtime typy.|
||`bool`|`bool`|16bitová logická hodnota.|
||`__wchar_t`|`char16`|16bitová nečíselná hodnota, která představuje bod kódu Unicode (UTF-16).|
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16bitové celé číslo se znaménkem.<br /><br /> 16bitová unsigned integer.|
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32 celé číslo se znaménkem.<br /><br /> 32 bitová unsigned integer.|
||`long long`ani`__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64 celé číslo se znaménkem.<br /><br /> 64 bitová unsigned integer.|
||`float, double`|`float32, float64`|32 nebo 754 64 číslo s plovoucí desetinnou čárkou ().|
||`enum {}`|`enum class {}`<br /><br /> -nebo-<br /><br /> `enum struct {}`|32-bit výčtu.|
||(Neplatí)|`Platform::Guid`|128 bitová nenumerická hodnota (GUID) v `Platform` oboru názvů.|
||`std::time_get`|`Windows::Foundation::DateTime`|Struktura data a času.|
||(Neplatí)|`Windows::Foundation::TimeSpan`|Struktura TimeSpan.|
||(Neplatí)|`Platform::Object^`|Základní objekt pro počítání referencí v C++ zobrazení prostředí Windows Runtimeho systému typů.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^`je odkazovaná, neproměnlivá, sekvence znaků Unicode, které reprezentují text.|
|Ukazatele|Ukazatel na objekt (`*`):<br /><br /> `std::shared_ptr`|Popisovač na objekt (`^`, vyslovit "Hat"):<br /><br /> *T ^ identifikátor*|Všechny třídy prostředí Windows Runtime jsou deklarovány pomocí modifikátoru "popisovač na objekt". K členům objektu se přistupuje pomocí operátoru šipky (`->`) třídy – Member-Access.<br /><br /> Modifikátor Hat znamená "ukazatel na objekt prostředí Windows Runtime, na který se automaticky počítá odkaz." Přesnější deklarace s popisovačem na objekt deklaruje, že by měl kompilátor vkládat kód pro automatické spravování počtu odkazů objektu a odstranění objektu, pokud počet odkazů přechází na nulu.|
|Reference|Odkaz na objekt (`&`):<br /><br /> *Identifikátor* *T* `&`|Sledovací odkaz (`%`):<br /><br /> *Identifikátor* *T* `%`|Pomocí modifikátoru sledování odkazů lze deklarovat pouze typy prostředí Windows Runtime. K členům objektu lze přistupovat pomocí operátoru tečka (`.`)-Member-Access.<br /><br /> Sledovací odkaz znamená "odkaz na objekt prostředí Windows Runtime, na který se automaticky počítá odkaz." Přesnější sledovací odkaz deklaruje, že by měl kompilátor vkládat kód pro automatické spravování počtu odkazů objektu a odstranění objektu, pokud počet odkazů přechází na nulu.|
|Dynamická deklarace typu|`new`|`ref new`|Přidělí objekt prostředí Windows Runtime a vrátí popisovač k tomuto objektu.|
|Správa životnosti objektů|`delete`*identifikátor*<br /><br /> `delete[]`  *RID*|(Vyvolá destruktor.)|Doba života je určena počítáním odkazů. Volání metody delete vyvolá destruktor, ale sám o sobě neuvolní paměť.|
|Deklarace pole|*Identifikátor T*`[]`<br /><br /> `std::array`*identifikátor*|`Array<`*Velikost* *identifikátoru* *T* `^>^` `(``)`<br /><br /> -nebo-<br /><br /> `WriteOnlyArray<`*Velikost* *identifikátoru* *T* `^>` `(`  `)`|Deklaruje jednorozměrné pole typu T ^ s možností pouze pro zápis. Samotné pole je také objektem s vypočítaným odkazem, který musí být deklarován pomocí modifikátoru "popisovač na objekt".<br /><br /> (Deklarace pole používají třídu hlaviček šablony, která je v `Platform` oboru názvů.)|
|Deklarace třídy|`class`  *identifikátor*`{}`<br /><br /> `struct`  *Identifikátor* `{}`|`ref class`  *Identifikátor* `{}`<br /><br /> `ref struct`  *Identifikátor* `{}`|Deklaruje běhovou třídu, která má výchozí privátní přístupnost.<br /><br /> Deklaruje běhovou třídu, která má výchozí přístupnost Public.|
|Deklarace struktury|`struct`  *Identifikátor* `{}`<br /><br /> (to znamená, že se jedná o jednoduchou starou datovou strukturu (POD))|`value class`  *Identifikátor* `{}`<br /><br /> `value struct`  *Identifikátor* `{}`|Deklaruje strukturu POD, která má výchozí privátní přístupnost.<br /><br /> Hodnotová třída může být reprezentovaná v metadatech Windows, ale C++ standardní třída nemůže být.<br /><br /> Deklaruje strukturu POD, která má výchozí veřejnou přístupnost.<br /><br /> Struktura hodnoty může být reprezentovaná v metadatech Windows, ale standardní C++ struktura nemůže být.|
|Deklarace rozhraní|abstraktní třída, která obsahuje pouze čistě virtuální funkce.|`interface class`  *Identifikátor* `{}`<br /><br /> `interface struct`  *Identifikátor* `{}`|Deklaruje rozhraní, které má výchozí privátní přístupnost.<br /><br /> Deklaruje rozhraní, které má výchozí veřejnou přístupnost.|
|Delegát|`std::function`|`public delegate`*návratový typ* *Delegate – identifikátor typu* *[parametry]* `(``);`|Deklaruje objekt, který lze vyvolat jako volání funkce.|
|Událost|(Neplatí)|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *Delegate – identifikátor typu* *identifikátor delegáta*  =  *Delegate –* identifikátortypu`( this` *[, parametry]* `ref new``);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> -nebo-<br /><br /> `EventRegistrationToken`*identifikátor tokenu* *událost obj*–identifikátor`+=` delegáta  = `.``;`<br /><br /> -nebo-<br /><br /> `auto`*identifikátor tokenu*  =  *obj*. *identifikátor události* `::add(` *identifikátor delegáta*`);`<br /><br /> *obj* identifikátor tokenu *identifikátoru události* `-=` `.``;`<br /><br /> -nebo-<br /><br /> *obj* identifikátor tokenu *identifikátoru události* `::remove(` `.``);`|Deklaruje objekt události, který ukládá kolekci obslužných rutin událostí (delegáty), které jsou volány při výskytu události.<br /><br /> Vytvoří obslužnou rutinu události.<br /><br /> Přidá obslužnou rutinu události.<br /><br /> Přidání obslužné rutiny události vrátí token události (*identifikátor token*). Pokud máte v úmyslu explicitně odebrat obslužnou rutinu události, je nutné uložit token události pro pozdější použití.<br /><br /> Odebere obslužnou rutinu události.<br /><br /> Chcete-li odebrat obslužnou rutinu události, je nutné zadat token události, který jste uložili při přidání obslužné rutiny události.|
|Vlastnost|(Neplatí)|`property` *Identifikátor*T;<br /><br /> `property` *T* *identifier* `[` *index* `];`<br /><br /> `property` *T* `default[` *index* `];`|Deklaruje, že členská funkce třídy nebo objektu je přístupná pomocí stejné syntaxe, která se používá pro přístup k datovému členu nebo indexovanému elementu pole.<br /><br /> Deklaruje vlastnost pro členskou funkci třídy nebo objektu.<br /><br /> Deklaruje indexovanou vlastnost u členské funkce objektu.<br /><br /> Deklaruje indexovanou vlastnost pro členskou funkci třídy.|
|Parametrizované typy|šablony|`generic <typename`*Identifikátor* *T* `> interface class``{}`<br /><br /> `generic <typename` T`> delegate` *[návratový typ]* *delegát – identifikátor*`() {}`|Deklaruje parametrizovanou třídu rozhraní.<br /><br /> Deklaruje parametrizovaného delegáta.|
|Typy hodnot s možnou hodnotou null|`boost::optional<T>`|[Platform:: iBox \<T >](../cppcx/platform-ibox-interface.md)|Umožňuje proměnným skalárních typů a struktur hodnot mít hodnotu `nullptr`.|

## <a name="see-also"></a>Viz také:

[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
