---
title: Stručná referenční dokumentace (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: eb407a0264a68f9b89e4a180c8b151076fdd109a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445328"
---
# <a name="quick-reference-ccx"></a>Stručná referenční dokumentace (C + +/ CX)

Modul Windows Runtime podporuje aplikace univerzální platformy Windows (UPW), které provést pouze v prostředí pro důvěryhodného operačního systému, použít oprávnění funkce, typy dat a zařízení a jsou distribuovány prostřednictvím Microsoft Store. C + +/ CX zjednodušují psaní aplikací pro Windows Runtime. Tento článek je Stručná referenční příručka; Podrobnější dokumentaci najdete v tématu [systém typů](../cppcx/type-system-c-cx.md).

Při sestavování v příkazovém řádku použít **/ZW** – možnost kompilátoru k sestavení aplikace pro UPW nebo součásti prostředí Windows Runtime. Pro přístup k prostředí Windows Runtime deklarace, které jsou definovány v souborech modulu Windows Runtime metadata (.winmd), zadejte `#using` směrnice nebo **/FU** – možnost kompilátoru. Když vytvoříte projekt pro aplikace pro UPW, Visual Studio ve výchozím nastavení nastaví tyto možnosti a přidá odkazy na všechny knihovny Windows Runtime.

## <a name="quick-reference"></a>Stručná referenční příručka

|Koncept|Standardní C++|C++/CX|Poznámky|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|Základní typy|Základní typy C++.|C + +/ CX základní typy, které implementují základní typy, které jsou definovány v modulu Windows Runtime.|`default` Obsahuje obor názvů C + +/ CX integrované, základní typy. Kompilátor implicitně mapuje C + +/ CX základní typy Standardní typy jazyka C++.<br /><br /> `Platform` Řadu oborů názvů obsahuje typy, které implementují základní typy modulu Windows Runtime.|
||`bool`|`bool`|Hodnotu typu Boolean. 8 bitů.|
||`__wchar_t`|`char16`|16bitové nečíselná hodnota, která představuje bod kódu Unicode (UTF-16).|
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16bitové celé číslo se znaménkem.<br /><br /> 16bitové celé číslo bez znaménka.|
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32bitové celé číslo se znaménkem.<br /><br /> 32bitové celé číslo bez znaménka.|
||`long long` - nebo - `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64bitové celé číslo se znaménkem.<br /><br /> 64bitové celé číslo bez znaménka.|
||`float, double`|`float32, float64`|32bitové nebo 64bitové IEEE 754 s plovoucí desetinnou čárkou číslo.|
||`enum {}`|`enum class {}`<br /><br /> -nebo-<br /><br /> `enum struct {}`|Výčet 32-bit.|
||(Netýká)|`Platform::Guid`|Hodnotu číselného typu 128-bit (GUID) v `Platform` oboru názvů.|
||`std::time_get`|`Windows::Foundation::DateTime`|Struktura datum a čas.|
||(Netýká)|`Windows::Foundation::TimeSpan`|Struktury timespan.|
||(Netýká)|`Platform::Object^`|Referenčně započítaný základního objektu v zobrazení C++ pro systém typů prostředí Windows Runtime.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` je počítáním referencí, nezměnitelný, sekvence znaků Unicode, které představují text.|
|Ukazatel|Ukazatel na objekt (`*`):<br /><br /> `std::shared_ptr`|Popisovač objektu (`^`, výslovnost "stříška"):<br /><br /> *T ^ identifikátor*|Všechny třídy Windows Runtime jsou deklarovány pomocí modifikátoru popisovač objektu. Členy objektu jsou přístupné pomocí šipky (`->`) – operátor přístupu členů třídy.<br /><br /> Modifikátor hat znamená "ukazatel na objekt prostředí Windows Runtime, který je automaticky odkaz počítají." Přesněji řečeno popisovač objektu deklaruje, že by měl kompilátor vložení kódu automaticky spravovat počet odkazů na objekt a objekt odstranit, pokud počet odkazů dosáhne nuly.|
|Odkaz|Odkaz na objekt (`&`):<br /><br /> *T* `&` *identifikátor*|Sledovací odkaz (`%`):<br /><br /> *T* `%` *identifikátor*|Pouze Windows Runtime, které typy mohou být deklarovány pomocí sledování odkazovat modifikátor. Členy objektu jsou přístupné pomocí tečka (`.`) – operátor přístupu členů třídy.<br /><br /> Sledovací odkaz znamená "odkaz na objekt prostředí Windows Runtime, který je automaticky počítáno referenčně." Přesněji řečeno sledovací odkaz deklaruje, že by měl kompilátor vložení kódu automaticky spravovat počet odkazů na objekt a objekt odstranit, pokud počet odkazů dosáhne nuly.|
|Dynamický typ deklarace|`new`|`ref new`|Objekt prostředí Windows Runtime přiděluje a poté vrátí popisovač do tohoto objektu.|
|Správa životního cyklu objektu|`delete` *identifikátor*<br /><br /> `delete[]`  *identifikátor*|(Vyvolá destruktor.)|Doba platnosti je určena počítání odkazů. Volání delete vyvolá destruktor, ale samotné neuvolní paměti.|
|Deklarace pole|*Identifikátor T* `[]`<br /><br /> `std::array` *identifikátor*|`Array<` *T* `^>^` *identifikátor* `(` *velikost* `)`<br /><br /> -nebo-<br /><br /> `WriteOnlyArray<` *T* `^>` *identifikátor* `(` *velikost* `)`|Deklaruje jednorozměrné pole upravitelné nebo jen pro zápis typu T ^. Pole samotného je také počítáním referencí objekt, který musí být deklarovány pomocí modifikátoru popisovač objektu.<br /><br /> (Používat záhlaví třída šablony, který je v deklarace pole `Platform` oboru názvů.)|
|Deklarace třídy|`class`  *identifikátor* `{}`<br /><br /> `struct`  *Identifikátor* `{}`|`ref class`  *Identifikátor* `{}`<br /><br /> `ref struct`  *Identifikátor* `{}`|Deklaruje třídu modulu runtime, který má výchozí přístupnost private.<br /><br /> Deklaruje třídu modulu runtime, který má výchozí přístupnost public.|
|Deklarace struktury|`struct`  *Identifikátor* `{}`<br /><br /> (to znamená, obyčejná stará Data strukturovat (POD))|`value class`  *Identifikátor* `{}`<br /><br /> `value struct`  *Identifikátor* `{}`|Deklaruje strukturu POD, který má výchozí přístupnost private.<br /><br /> Hodnotová třída může být reprezentovaná v metadatech Windows, ale nemůže být standardní třídy jazyka C++.<br /><br /> Deklaruje strukturu POD, který má výchozí přístupnost public.<br /><br /> Hodnota strukturu může být reprezentovaná v metadatech Windows, ale nemůže být standardní struktury C++.|
|Deklarace rozhraní|abstraktní třída, která obsahuje pouze čistě virtuální funkce.|`interface class`  *Identifikátor* `{}`<br /><br /> `interface struct`  *Identifikátor* `{}`|Deklaruje rozhraní, která má výchozí přístupnost private.<br /><br /> Deklaruje rozhraní, která má výchozí přístupnost public.|
|Delegát|`std::function`|`public delegate` *Návratový typ* *identifikátor typu delegáta* `(` *[parametry]* `);`|Deklaruje objekt, který lze vyvolat jako volání funkce.|
|Událost|(Netýká)|`event` *identifikátor typu delegáta* *identifikátor události* `;`<br /><br /> *identifikátor typu delegáta* *delegáta identifikátor* = `ref new`*identifikátor typu delegáta*`( this`*[, parametry]*`);`<br /><br /> *identifikátor události* `+=` *identifikátor delegáta* `;`<br /><br /> -nebo-<br /><br /> `EventRegistrationToken` *Token identifikátoru* = *obj*`.`*identifikátor události*`+=`*identifikátor delegáta*`;`<br /><br /> -nebo-<br /><br /> `auto` *Token identifikátoru* = *obj*. *identifikátor události*`::add(`*identifikátor delegáta*`);`<br /><br /> *obj* `.` *identifikátor události* `-=` *token identifikátor* `;`<br /><br /> -nebo-<br /><br /> *obj* `.` *identifikátor události* `::remove(` *token identifikátor* `);`|Deklaruje objekt události, která uloží kolekci obslužných rutin událostí (delegátů), které jsou volány při výskytu události.<br /><br /> Vytvoří obslužnou rutinu události.<br /><br /> Přidá obslužnou rutinu události.<br /><br /> Přidání obslužné rutiny události vrátí token událostí (*token identifikátor*). Pokud chcete explicitně odebrat obslužnou rutinu události, je nutné uložit události token pro pozdější použití.<br /><br /> Odebere obslužnou rutinu události.<br /><br /> Chcete-li odebrat obslužnou rutinu události, je nutné zadat token událostí, který jste uložili při přidání obslužné rutiny události.|
|Vlastnost|(Netýká)|`property` *T* *identifikátor*;<br /><br /> `property` *T* *identifikátor* `[` *indexu* `];`<br /><br /> `property` *T* `default[` *indexu* `];`|Deklaruje, že členská třída nebo objekt lze přistupovat pomocí stejné syntaxe, která se používá pro přístup k datový člen nebo indexovaného prvku pole.<br /><br /> Deklaruje vlastnost u členské funkce třídy nebo objektu.<br /><br /> Deklaruje indexovanou vlastnost na členskou funkci objektu.<br /><br /> Deklaruje indexovanou vlastnost u členské funkce třídy.|
|Parametrizované typy|šablony|`generic <typename` *T* `> interface class` *identifikátor* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[návratového typu]* *identifikátor delegáta* `() {}`|Deklaruje třídu parametrizované rozhraní.<br /><br /> Deklaruje parametry delegáta.|
|Typy s možnou hodnotou Null|`boost::optional<T>`|[Platform::ibox – \<T >](../cppcx/platform-ibox-interface.md)|Umožňuje proměnné Skalární typy a struktury hodnotu s hodnotou `nullptr`.|

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)