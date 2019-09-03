---
title: '#using – direktiva (C++/CLI)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220195"
---
# <a name="using-directive-ccli"></a>#usingská směrniceC++(/CLI)

Importuje metadata do programu zkompilovaného pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Syntaxe

> **#using** *soubor* [**as_friend**]

### <a name="parameters"></a>Parametry

*souborů*\
Knihovna DLL, .exe, .netmodule, nebo .obj jazyka MSIL. Například

`#using <MyComponent.dll>`

**as_friend**\
Určuje, že všechny typy v *souboru* jsou přístupné. Další informace naleznete v tématu [Friend Assemblies (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Poznámky

*soubor* může být soubor jazyka MSIL (Microsoft Intermediate Language), který importujete pro spravovaná data a spravované konstrukce. Pokud soubor. dll obsahuje manifest sestavení, pak jsou importovány všechny knihovny DLL, na které je odkazováno v manifestu, a sestavení, které vytváříte, zobrazí *soubor* v metadatech jako odkaz na sestavení.

Pokud *soubor* neobsahuje sestavení (Pokud *soubor* je modul) a pokud nechcete použít informace o typu z modulu v aktuální aplikaci (sestavení), máte možnost přesně určit, že modul je součástí sestavení; použijte [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy z modulu pak budou k dispozici pro všechny aplikace, které odkazují na sestavení.

Alternativou k použití **#using** je možnost kompilátoru [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

sestavení. exe předaná **#using** by měla být kompilována pomocí jednoho z kompilátorů aplikace .NET Visual Studio (například Visual Basic C#nebo vizuálu).  Při pokusu o import metadat ze sestavení .exe kompilovaného s `/clr` dojde k výjimce načítání souboru.

> [!NOTE]
> Komponentu, na kterou je odkazováno pomocí **#using** lze spustit s jinou verzí souboru importovaným v době kompilace, což způsobí, že klientská aplikace poskytne neočekávané výsledky.

Aby kompilátor rozpoznal typ v sestavení (ne v modulu), musí být vynucen přeložit typ. Můžete ji vynutit například definováním instance typu. Existují i jiné způsoby, jak přeložit názvy typů v sestavení pro kompilátor. Například Pokud převezmete z typu v sestavení, název typu bude pro kompilátor znám.

Při importu metadat sestavených ze zdrojového kódu, který použil [__declspec (thread)](../cpp/thread.md), sémantika vlákna není v metadatech trvalá. Například Proměnná deklarovaná pomocí **__declspec (thread)** , kompilována v programu sestaveném pro .NET Framework modul CLR (Common Language Runtime) a pak importována prostřednictvím **#using**, nebude mít sémantiku **__declspec (thread)** pro proměnnou.

Všechny importované typy (spravované i nativní) v souboru, na který odkazuje **#using** jsou k dispozici, ale Kompilátor považuje nativní typy za deklarace, nikoli definice.

Soubor mscorlib.dll je při kompilaci s `/clr` odkazován automaticky.

Proměnná prostředí LIBPATH určuje adresáře, které se mají hledat, když Kompilátor přeloží názvy souborů předaných do **#using**.

Kompilátor vyhledá odkazy podél následující cesty:

- Cesta zadaná v příkazu **#using** .

- Aktuální adresář.

- Systémový adresář rozhraní .NET Framework.

- Adresáře přidané pomocí možnosti kompilátoru [/AI](../build/reference/ai-specify-metadata-directories.md) .

- Adresáře dle proměnné prostředí LIBPATH.

## <a name="example"></a>Příklad

Pokud sestavíte sestavení (C) a odkazujete na sestavení (B), které odkazuje na jiné sestavení (A), nebudete muset explicitně odkazovat na sestavení A, pokud explicitně nepoužijete jeden z typů typu v jazyce C.

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

V následující ukázce není k dispozici žádná chyba kompilátoru pro neodkazování na *using_assembly_A. dll*, protože program nepoužívá žádný z typů definovaných v *using_assembly_A. cpp*.

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

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
