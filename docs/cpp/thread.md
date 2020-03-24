---
title: vlákno
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 30972b5668d3eab9ec2118f3d90d7ced1e087275
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160694"
---
# <a name="thread"></a>vlákno

**Specifické pro společnost Microsoft**

Modifikátor třídy úložiště rozšířených **vlákny** slouží k deklaraci proměnné Thread Local. V případě přenosného ekvivalentu v C++ 11 a novějších používejte specifikátor třídy úložiště [thread_local](../cpp/storage-classes-cpp.md#thread_local) pro přenos přenosného kódu. V systému Windows **thread_local** je implementována s **__declspec (thread)** .

## <a name="syntax"></a>Syntaxe

**__declspec (thread)** *deklarátor*

## <a name="remarks"></a>Poznámky

Místní úložiště vláken (TLS) je mechanismus, podle kterého všechna vlákna procesu alokují prostor pro data určitého vlákna. U standardních aplikací s více vlákny jsou data sdílena mezi všemi vlákny daného procesu, kde místní úložiště vláken představuje mechanismus pro rozdělení dat pro vlákno. Úplný popis vláken naleznete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deklarace thread local proměnných musí použít [syntaxi rozšířeného atributu](../cpp/declspec.md) a klíčové slovo **__declspec** s klíčovým slovem **thread** . Například následující kód deklaruje celočíselnou thread local proměnnou a inicializuje ji hodnotou:

```cpp
__declspec( thread ) int tls_i = 1;
```

Při použití proměnných místního vlákna v dynamicky načtených knihovnách je nutné znát faktory, které mohou způsobit, že místní proměnná vlákna nebude inicializována správně:

1. Je-li proměnná inicializována voláním funkce (včetně konstruktorů), tato funkce bude volána pouze pro vlákno, které způsobilo načtení binárního souboru nebo knihovny DLL do procesu, a pro ta vlákna, která byla spuštěna po načtení binárního souboru nebo knihovny DLL. Inicializační funkce nejsou volány pro žádné jiné vlákno, které již bylo spuštěno při načtení knihovny DLL. K dynamické inicializaci dojde u volání DllMain pro DLL_THREAD_ATTACH, ale knihovna DLL tuto zprávu nikdy nezíská, pokud knihovna DLL není v procesu, kdy je vlákno spuštěno.

1. Místní proměnné vlákna, které jsou inicializovány staticky s konstantními hodnotami jsou obvykle inicializovány správně na všech vláknech. Od prosince 2017 však existuje známý problém s dodržováním v kompilátoru společnosti Microsoft C++ , který proměnné **constexpr** obdrží dynamickým spíše než statickou inicializací.

   Poznámka: v budoucích aktualizacích kompilátoru se očekává, že oba tyto problémy jsou vyřešené.

Kromě toho je nutné při deklaraci thread local objektů a proměnných pozorovat tyto pokyny:

- Atribut **thread** lze použít pouze na deklarace tříd a dat a definice; **vlákno** nelze použít pro deklarace a definice funkcí.

- Atribut **vlákna** lze zadat pouze pro datové položky s trváním statického úložiště. To zahrnuje globální datové objekty ( **static** i **extern**), místní statické objekty a statické datové členy tříd. Nelze deklarovat automatické datové objekty s atributem **thread** .

- Je nutné použít atribut **thread** pro deklaraci a definici objektu Thread Local, zda se deklarace a definice vyskytují ve stejném souboru nebo samostatných souborech.

- Atribut **thread** nelze použít jako modifikátor typu.

- Vzhledem k tomu, že deklarace objektů, které používají atribut **thread** , jsou povoleny, tyto dva příklady jsou sémanticky ekvivalentní:

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- Standard jazyka C umožňuje inicializaci objektu nebo proměnné s výrazem, který zahrnuje odkaz sám na sebe, ale pouze pro nestatické objekty. Přestože C++ obvykle umožňuje takovou dynamickou inicializaci objektu s výrazem, který zahrnuje odkaz sám na sebe, tento typ inicializace není povolen u Thread localch objektů. Příklad:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Výraz **sizeof** , který obsahuje inicializovaný objekt, nepředstavuje odkaz sám na sebe a je povolen v C a C++.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Úložiště Thread Local (TLS)](../parallel/thread-local-storage-tls.md)
