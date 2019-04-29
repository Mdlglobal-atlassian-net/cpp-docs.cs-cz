---
title: '#Using – direktiva (C++vyhodnocovací)'
ms.date: 10/18/2018
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: ddae6137e94e10f5701e1e7d0f8f7a7514b18662
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383877"
---
# <a name="using-directive-ccli"></a>#using – direktiva (C++vyhodnocovací)

Importuje metadata do programu kompilovaného s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Syntaxe

```
#using file [as_friend]
```

### <a name="parameters"></a>Parametry

*Soubor*<br/>
Knihovna DLL, .exe, .netmodule, nebo .obj jazyka MSIL. Například

`#using <MyComponent.dll>`

*as_friend*<br/>
Určuje, že všechny typy v *soubor* jsou k dispozici. Další informace najdete v tématu [přátelská sestavení (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Poznámky

*soubor* může být Microsoft intermediate language (MSIL) soubor, který importujete pro své spravované konstrukce a spravovaná data. Pokud soubor DLL obsahuje manifest sestavení, potom jsou importovány všechny odkazované sestavované a zobrazí se seznam sestavení, kterou vytváříte *souboru* v metadatech jako odkaz na sestavení.

Pokud *souboru* neobsahuje sestavení (Pokud *souboru* je modul) a pokud je nemáte v úmyslu použít informace o typu z modulu v aktuální aplikaci (sestavení), máte možnost pouze označující, že modul je součástí sestavení použít [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy z modulu pak budou k dispozici pro všechny aplikace, které odkazují na sestavení.

Alternativou k použití **#using** je [/FU](../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru.

sestavení .exe předaná **#using** by měl být zkompilován pomocí jedné z kompilátorů aplikace Visual Studio .NET (Visual Basic nebo Visual C#, například).  Při pokusu o import metadat ze sestavení .exe kompilovaného s `/clr` dojde k výjimce načítání souboru.

> [!NOTE]
> Komponenta, která je odkazována pomocí **#using** můžete spustit s jinou verzí souboru v době kompilace, což způsobí klientská aplikace poskytne neočekávané výsledky.

Je-li nutné, aby kompilátor rozpoznával typ v sestavení (ne modul), je zapotřebí jej donutit k přeložení typu, což lze provést například definováním instance daného typu. Existují jiné způsoby přeložení názvů typů pro kompilátor v sestavení, název typu se například stane pro kompilátor známým, pokud je zděděn z typu v sestavení.

Při importu metadat ze zdrojového kódu, který používá [__declspec(thread)](../cpp/thread.md), sémantika vláken nejsou zachované v metadatech. Například proměnná deklarovaná pomocí **__declspec(thread)** zkompilovaná v programu, který je sestaven pro modul common language runtime rozhraní .NET Framework a poté importována pomocí **#using**, už nebude mít **__declspec(thread)** sémantiky pro proměnnou.

Všechny importované typy (spravované a nativní) v souboru odkazovaného atributem **#using** jsou k dispozici, ale kompilátor zpracovává nativní typy jako deklarace, nikoli definice.

Soubor mscorlib.dll je při kompilaci s `/clr` odkazován automaticky.

Proměnné prostředí LIBPATH Určuje adresáře, které se bude vyhledávat při kompilátor pokusí přeložit názvy souborů předaných **#using**.

Kompilátor bude hledat odkazy v následující cestě:

- Cesta zadaná v **#using** příkazu.

- Aktuální adresář.

- Systémový adresář rozhraní .NET Framework.

- Adresáře přidané pomocí [/AI](../build/reference/ai-specify-metadata-directories.md) – možnost kompilátoru.

- Adresáře dle proměnné prostředí LIBPATH.

## <a name="example"></a>Příklad

Při vytvoření sestavení (C) a odkázání na sestavení (B), které odkazuje na jiné sestavení (A), nebude explicitně odkazováno na sestavení A, pokud nebude v sestavení C explicitně použit jeden z typů sestavení A.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>Příklad

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>Příklad

V následující ukázce se nevyskytuje žádná chyba kompilátoru v souvislosti s neodkazováním na using_assembly_A.dll, protože program nepoužívá žádné typy definované v using_assembly_A.cpp.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>Viz také:

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)