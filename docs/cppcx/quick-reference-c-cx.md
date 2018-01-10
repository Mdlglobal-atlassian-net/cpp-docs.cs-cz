---
title: "Stručná referenční dokumentace (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
caps.latest.revision: "31"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b34c0d36c33652ecbef3a1af745015d92fc05f3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="quick-reference-ccx"></a>Stručná referenční dokumentace (C + +/ CX)
Prostředí Windows Runtime podporuje aplikace pro univerzální platformu Windows, které provést pouze v prostředí trustworthy operačního systému, použijte oprávnění funkce, datové typy a zařízení a jsou distribuovány prostřednictvím [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]. C + +/ CX zjednodušit psaní aplikací pro prostředí Windows Runtime. Tento článek je rychlý přehled; Podrobnější dokumentaci najdete v tématu [systém typů](../cppcx/type-system-c-cx.md) a [rozšíření komponent pro platformy běhového prostředí](http://go.microsoft.com/fwlink/p/?linkid=228720).  
  
 Při sestavování na příkazovém řádku použít **/ZW** – možnost kompilátoru sestavit aplikaci pro univerzální platformu Windows nebo prostředí Windows Runtime součásti. Pro přístup k prostředí Windows Runtime deklarace, které jsou definovány v souborech metadat (.winmd) prostředí Windows Runtime, zadejte `#using` – direktiva nebo **/FU** – možnost kompilátoru. Při vytváření projektu pro univerzální platformu Windows aplikaci Visual Studio ve výchozím nastavení nastaví tyto možnosti a přidá odkazy na všechny knihovny prostředí Windows Runtime.  
  
## <a name="quick-reference"></a>Stručná referenční příručka  
  
|Koncept|Standardní C++|C++/CX|Poznámky|  
|-------------|--------------------|------------------------------------------------------------------|-------------|  
|Základní typy|Základní typy C++.|C + +/ CX základní typy, které implementují základní typy, které jsou definovány v prostředí Windows Runtime.|`default` Obor názvů obsahuje C + +/ CX předdefinované, základní typy. Kompilátor implicitně mapuje C + +/ CX základní typy na standardní typy C++.<br /><br /> `Platform` Řadu obory názvů obsahuje typy, které implementují základní typy prostředí Windows Runtime.|  
||`bool`|`bool`|8bitové logická hodnota.|  
||`__wchar_t`|`char16`|Hodnota číselného typu 16bitové, který představuje bod kódování Unicode (UTF-16).|  
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16bitové znaménkem.<br /><br /> 16bitové celé číslo bez znaménka.|  
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32-bit znaménkem.<br /><br /> 32bitové celé číslo bez znaménka.|  
||`long long`- nebo -`__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64bitová verze znaménkem.<br /><br /> 64bitové celé číslo bez znaménka.|  
||`float, double`|`float32, float64`|32bitové nebo 64bitové IEEE 754 s plovoucí desetinnou čárkou číslo.|  
||`enum {}`|`enum class {}`<br /><br /> -nebo-<br /><br /> `enum struct {}`|32-bit výčtu.|  
||(Nevztahuje)|`Platform::Guid`|Hodnotu číselného typu 128-bit (GUID) do `Platform` oboru názvů.|  
||`std::time_get`|`Windows::Foundation::DateTime`|Struktura data a času.|  
||(Nevztahuje)|`Windows::Foundation::TimeSpan`|Struktura časové rozpětí.|  
||(Nevztahuje)|`Platform::Object^`|Počítá se odkaz na základní objekt v zobrazení C++ prostředí Windows Runtime typ systému.|  
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^`je pořadí počítá odkaz, neměnné, znaky Unicode, které představují text.|  
|Ukazatele|Ukazatel na objekt (`*`):<br /><br /> `std::shared_ptr`|Popisovač objektu (`^`, vyslovováno "hat"):<br /><br /> *T ^ identifikátor*|Všechny třídy prostředí Windows Runtime jsou deklarovány s použitím modifikátor popisovač objektu. Členové objektu přistupují pomocí šipku (`->`) operátor přístup člena třídy.<br /><br /> Modifikátor hat znamená "ukazatel na objekt prostředí Windows Runtime, který je automaticky odkaz počítají." Přesněji řečeno popisovač objektu prohlašuje, že by měl kompilátor vložení kódu automaticky spravovat počet odkazů objekt a objekt odstranit, pokud počet odkazů přejde na hodnotu nula.|  
|Odkaz|Odkaz na objekt (`&`):<br /><br /> *T* `&` *identifikátor*|Sledovací odkaz (`%`):<br /><br /> *T* `%` *identifikátor*|Jenom prostředí Windows Runtime, které typy lze deklarovat pomocí sledování referenční modifikátor. Členové objektu přistupují pomocí tečky (`.`) operátor přístup člena třídy.<br /><br /> Sledovací odkaz znamená "odkaz na objekt prostředí Windows Runtime, který je automaticky odkaz, na které se mají spočítat." Přesněji řečeno sledovací odkaz prohlašuje, že by měl kompilátor vložení kódu automaticky spravovat počet odkazů objekt a objekt odstranit, pokud počet odkazů přejde na hodnotu nula.|  
|dynamický typ deklarace|`new`|`ref new`|Přiděluje objekt prostředí Windows Runtime a vrátí popisovač pro tento objekt.|  
|Správa životního cyklu objektu|`delete`*identifikátor*<br /><br /> `delete[]`  *identifikátor*|(Vyvolá destruktoru.)|Doba platnosti je určen podle počítání odkazů. Volání odstranit vyvolá destruktoru ale samotné není volné paměti.|  
|Deklarace pole|*Identifikátor T*`[]`<br /><br /> `std::array`*identifikátor*|`Array<`*T* `^>^` *identifier* `(` *size*`)`<br /><br /> -nebo-<br /><br /> `WriteOnlyArray<`*T* `^>`*identifier* `(` *size*  `)`|Deklaruje jednorozměrné pole upravitelnými nebo jen pro zápis typu t. ^. Pole, samotné je také počítá odkaz na objekt, který musí být deklarován pomocí modifikátoru popisovač objektu.<br /><br /> (Deklarace pole použití třídy záhlaví šablony, která je v `Platform` oboru názvů.)|  
|Deklarace třídy|`class`  *identifikátor*`{}`<br /><br /> `struct`*identifikátor*`{}`|`ref class`*identifikátor*`{}`<br /><br /> `ref struct`*identifikátor*`{}`|Deklaruje runtime třídy, která má výchozí privátní usnadnění.<br /><br /> Deklaruje runtime třídy, která má výchozí veřejnou dostupnost.|  
|Deklarace struktury|`struct`*identifikátor*`{}`<br /><br /> (to znamená, prostý stará Data struktury (POD))|`value class`*identifikátor*`{}`<br /><br /> `value struct`*identifikátor*`{}`|Deklaruje POD struktura, která má výchozí privátní usnadnění.<br /><br /> – Hodnotová třída může být reprezentován v metadatech systému Windows, ale nemůže být třídu standardní C++.<br /><br /> Deklaruje POD struktura, která má výchozí veřejnou dostupnost.<br /><br /> Struktury hodnotu může být reprezentován v metadatech systému Windows, ale nemůže být standardní C++ struktury.|  
|deklarace rozhraní|abstraktní třída, která obsahuje jenom čistý virtuální funkce.|`interface class`*identifikátor*`{}`<br /><br /> `interface struct`*identifikátor*`{}`|Deklaruje rozhraní, které má výchozí privátní usnadnění.<br /><br /> Deklaruje rozhraní, které má výchozí veřejnou dostupnost.|  
|Delegát|`std::function`|`public delegate`*návratový typ* *identifikátor typu delegáta* `(` *[parametry]*`);`|Deklaruje objekt, který lze vyvolat jako volání funkce.|  
|Událost|(Nevztahuje)|`event`*identifikátor typu delegáta* *identifikátor události*`;`<br /><br /> *identifikátor typu delegáta* *delegáta identifikátor* = `ref new`*identifikátor typu delegáta*`( this`*[, parametry]*`);`<br /><br /> *identifikátor události* `+=` *delegáta identifikátor*`;`<br /><br /> -nebo-<br /><br /> `EventRegistrationToken`*token identifikátor* = *obj*`.`*identifikátor události*`+=`*identifikátor delegáta*`;`<br /><br /> -nebo-<br /><br /> `auto`*token identifikátor* = *obj*. *identifikátor události*`::add(`*identifikátor delegáta*`);`<br /><br /> *obj* `.` *identifikátor události* `-=` *token identifikátor*`;`<br /><br /> -nebo-<br /><br /> *obj* `.` *identifikátor události* `::remove(` *token identifikátor*`);`|Deklaruje objekt události, která ukládá kolekce obslužné rutiny (delegáti), které jsou volány při výskytu události.<br /><br /> Vytvoří obslužnou rutinu události.<br /><br /> Přidá obslužnou rutinu události.<br /><br /> Přidání obslužné rutiny události vrátí token událostí (*token identifikátor*). Pokud máte v úmyslu explicitně odeberte obslužné rutiny události, je nutné uložit token událostí pro pozdější použití.<br /><br /> Odebere obslužnou rutinu.<br /><br /> Odebrat obslužné rutiny události, je nutné zadat událostí token, který jste uložili při přidání obslužné rutiny události.|  
|Vlastnost|(Nevztahuje)|`property`*T* *identifier*;<br /><br /> `property`*T* *identifier* `[` *index*`];`<br /><br /> `property`*T* `default[` *index*`];`|Deklaruje, že členské funkce tříd nebo objektů přistupuje pomocí stejné syntaxi, která se má použít pro přístup ke členu dat nebo indexované element pole.<br /><br /> Deklaruje vlastnost na členské funkce tříd nebo objektů.<br /><br /> Indexované vlastnosti deklaruje na členskou funkci objektu.<br /><br /> Indexované vlastnosti deklaruje na členské funkce tříd.|  
|Parametrizované typy|šablony|`generic <typename`*T* `> interface class` *identifier*`{}`<br /><br /> `generic <typename`*T* `> delegate` *[návratový typ]* *delegáta identifikátor*`() {}`|Deklaruje třídu parametrizované rozhraní.<br /><br /> Deklaruje parametrizované delegáta.|  
|typy hodnot s povolenou hodnotou Null|`boost::optional<T>`|[Platform::IBox \<T >](../cppcx/platform-ibox-interface.md)|Umožňuje proměnné Skalární typy a struktury hodnotu tak, aby měl hodnotu `nullptr`.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)