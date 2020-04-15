---
title: Anotační parametry funkce a vrácené hodnoty
description: Referenční příručka pro parametr funkce a poznámky vrácené hodnoty.
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328001"
---
# <a name="annotating-function-parameters-and-return-values"></a>Anotační parametry funkce a vrácené hodnoty

Tento článek popisuje typické použití anotací pro jednoduché parametry funkce – skalára a ukazatele na struktury a třídy – a většinu druhů vyrovnávacích pamětí. Tento článek také zobrazuje běžné vzory použití pro poznámky. Další poznámky související s funkcemi naleznete v [tématu Anotating function behavior](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Parametry ukazatele

Pro poznámky v následující tabulce, když je parametr ukazatele anotován, analyzátor hlásí chybu, pokud je ukazatel null. Tato anotace se vztahuje na ukazatele a na všechny datové položky, na které je odkazováno.

### <a name="annotations-and-descriptions"></a>Poznámky a popisy

- `_In_`

     Anotuje vstupní parametry, které jsou skaláky, struktury, ukazatele na struktury a podobně. Explicitně mohou být použity na jednoduché skalár. Parametr musí být platný v předběžném stavu a nebude změněn.

- `_Out_`

     Anotuje výstupní parametry, které jsou skaláky, struktury, ukazatele na struktury a podobně. Neaplikujte tuto poznámku na objekt, který nemůže vrátit hodnotu – například skalár, který je předán hodnotou. Parametr nemusí být platný v předběžném stavu, ale musí být platný v post-state.

- `_Inout_`

     Anotuje parametr, který bude změněn funkcí. Musí být platný v pre-state a post-state, ale předpokládá se, že mají různé hodnoty před a po volání. Musí se vztahovat na upravitelnou hodnotu.

- `_In_z_`

     Ukazatel na řetězec s ukončeným hodnotou null, který se používá jako vstup. Řetězec musí být platný v předběžném stavu. Upřednostňují se `PSTR`varianty aplikace , které již mají správné poznámky.

- `_Inout_z_`

     Ukazatel na pole znaků ukončené nulou, které bude změněno. Musí být platný před a po volání, ale předpokládá se, že hodnota se změnila. Null zakončení může být přesunuta, ale pouze prvky až původní null zakončení lze přistupovat.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Ukazatel na pole, které je čteno funkcí. Pole je velikostprvky, `s` které musí být všechny platné.

     Varianta `_bytes_` udává velikost v bajtů namísto prvků. Tuto variantu použijte pouze v případě, že velikost nelze vyjádřit jako prvky. Řetězce by `char` například použít `_bytes_` variantu pouze v `wchar_t` případě, že podobné funkce, která používá by.

- `_In_reads_z_(s)`

     Ukazatel na pole, které je ukončeno hodnotou null a má známou velikost. Prvky až do zakončení `s` null – nebo pokud není null zakončení – musí být platný v pre-state. Pokud je velikost známa v `s` bajtech, měřítko podle velikosti prvku.

- `_In_reads_or_z_(s)`

     Ukazatel na pole, které je ukončeno hodnotou null nebo má známou velikost nebo obojí. Prvky až do zakončení `s` null – nebo pokud není null zakončení – musí být platný v pre-state. Pokud je velikost známa v `s` bajtech, měřítko podle velikosti prvku. (Používá se `strn` pro rodinu.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Ukazatel na pole `s` prvků (resp. bajtů), které budou zapsány funkce. Prvky pole nemusí být platné v předběžném stavu a počet prvků, které jsou platné v post-state, není určen. Pokud jsou poznámky na typ parametru, jsou použity v post-state. Zvažte například následující kód.

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     V tomto příkladu volající poskytuje `size` vyrovnávací `p1`paměť prvků pro . `MyStringCopy`některé z těchto prvků jsou platné. Ještě důležitější je, `_Null_terminated_` že `PWSTR` anotace na znamená, že `p1` je null ukončena v post-state. Tímto způsobem počet platných prvků je stále dobře definován, ale není vyžadován počet určitý prvek.

     Varianta `_bytes_` udává velikost v bajtů namísto prvků. Tuto variantu použijte pouze v případě, že velikost nelze vyjádřit jako prvky. Řetězce by `char` například použít `_bytes_` variantu pouze v `wchar_t` případě, že podobné funkce, která používá by.

- `_Out_writes_z_(s)`

     Ukazatel na pole `s` prvků. Prvky nemusí být platné v pre-state. V post-state musí být platné prvky prostřednictvím zakončení null , které musí být k dispozici. Pokud je velikost známa v `s` bajtech, měřítko podle velikosti prvku.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Ukazatel na pole, které je přečteno i zapsáno do funkce. Je to velikostní `s` prvky a je platný v představu a po stavu.

     Varianta `_bytes_` udává velikost v bajtů namísto prvků. Tuto variantu použijte pouze v případě, že velikost nelze vyjádřit jako prvky. Řetězce by `char` například použít `_bytes_` variantu pouze v `wchar_t` případě, že podobné funkce, která používá by.

- `_Inout_updates_z_(s)`

     Ukazatel na pole, které je ukončeno s nulou a má známou velikost. Prvky prostřednictvím zakončení null – které musí být k dispozici – musí být platné v pre-state a post-state. Hodnota v post-state se předpokládá, že se liší od hodnoty v pre-state; , který zahrnuje umístění zakončení null. Pokud je velikost známa v `s` bajtech, měřítko podle velikosti prvku.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ukazatel na pole `s` prvků. Prvky nemusí být platné v pre-state. V post-state musí být `c`platné prvky až do elementu -th. Variantu `_bytes_` lze použít, pokud je velikost známa v bajtů, nikoli v počtu prvků.

     Příklad:

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ukazatel na pole, které je čteno i zapsáno funkcí. Je to velikost `s` prvky, které musí být platné v `c` pre-state a prvky musí být platné v post-state.

     Varianta `_bytes_` udává velikost v bajtů namísto prvků. Tuto variantu použijte pouze v případě, že velikost nelze vyjádřit jako prvky. Řetězce by `char` například použít `_bytes_` variantu pouze v `wchar_t` případě, že podobné funkce, která používá by.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Ukazatel na pole, které je čteno i zapsáno funkcí prvků velikosti. `s` Definováno jako rovnocenné:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Jinými slovy každý prvek, který existuje `s` ve vyrovnávací paměti až v pre-state je platný v pre-state a post-state.

     Varianta `_bytes_` udává velikost v bajtů namísto prvků. Tuto variantu použijte pouze v případě, že velikost nelze vyjádřit jako prvky. Řetězce by `char` například použít `_bytes_` variantu pouze v `wchar_t` případě, že podobné funkce, která používá by.

- `_In_reads_to_ptr_(p)`

     Ukazatel na pole, `p - _Curr_` `p` pro které (to znamená minus `_Curr_`) je platný výraz. Prvky `p` před musí být platné v předběžném stavu.

    Příklad:

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Ukazatel na pole ukončené hodnotou `p - _Curr_` null, `p` pro `_Curr_`které je výraz (tj. minus ) platným výrazem. Prvky `p` před musí být platné v předběžném stavu.

- `_Out_writes_to_ptr_(p)`

     Ukazatel na pole, `p - _Curr_` `p` pro které (to znamená minus `_Curr_`) je platný výraz. Prvky `p` před nemusí být platné v pre-state a musí být platné v post-state.

- `_Out_writes_to_ptr_z_(p)`

     Ukazatel na pole ukončené hodnotou `p - _Curr_` null, `p` pro `_Curr_`které (tj. mínus) je platný výraz. Prvky `p` před nemusí být platné v pre-state a musí být platné v post-state.

## <a name="optional-pointer-parameters"></a>Volitelné parametry ukazatele

Pokud obsahuje `_opt_`anotaci parametru ukazatele , znamená to, že parametr může být null. V opačném případě se poznámky chovají stejně jako verze, která neobsahuje `_opt_`. Zde je seznam `_opt_` variant anotací parametrů ukazatele:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parametry výstupního ukazatele

Výstupní ukazatel parametry vyžadují speciální zápis k rozdvojení nullness na parametr a špičaté umístění.

### <a name="annotations-and-descriptions"></a>Poznámky a popisy

- `_Outptr_`

   Parametr nemůže mít hodnotu null a v post-stavu umístění s odkazem na hodnotu nemůže být null a musí být platné.

- `_Outptr_opt_`

   Parametr může být null, ale v post-state umístění špičaté na nemůže být null a musí být platný.

- `_Outptr_result_maybenull_`

   Parametr nemůže mít hodnotu null a v post-stavu může být umístění s odkazem na hodnotu null.

- `_Outptr_opt_result_maybenull_`

   Parametr může být null a v post-state umístění s odkazem na pozici může být null.

  V následující tabulce jsou do názvu poznámky vloženy další podřetězce, aby se dále kvalifikoval význam poznámky. Různé podřetězce jsou `_z` `_COM_`, `_buffer_` `_bytebuffer_`, `_to_`, a .

> [!IMPORTANT]
> Pokud rozhraní, které anotujete, je COM, použijte formulář COM těchto poznámk. Nepoužívejte poznámky COM s jiným rozhraním typu.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   Vrácený ukazatel `_Null_terminated_` má poznámku.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Vrácený ukazatel má sémantiku COM `_On_failure_` a proto nese post podmínku, že vrácený ukazatel je null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť prvků velikosti `s` nebo bajtů.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Vrácený ukazatel odkazuje na `s` vyrovnávací paměť velikosti prvků nebo `c` bajtů, z nichž první jsou platné.

Některé konvence rozhraní předpokládají, že výstupní parametry jsou zrušeny při selhání. S výjimkou explicitně kódu MODELU COM jsou upřednostňovány formuláře v následující tabulce. Pro kód MODELU COM použijte odpovídající formuláře MODELU COM, které jsou uvedeny v předchozí části.

- `_Result_nullonfailure_`

   Upravuje další poznámky. Výsledek je nastaven na hodnotu null, pokud se funkce nezdaří.

- `_Result_zeroonfailure_`

   Upravuje další poznámky. Výsledek je nastaven na nulu, pokud funkce selže.

- `_Outptr_result_nullonfailure_`

   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo null, pokud se funkce nezdaří. Tato anotace je pro nevolitelný parametr.

- `_Outptr_opt_result_nullonfailure_`

   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo null, pokud se funkce nezdaří. Tato anotace je pro volitelný parametr.

- `_Outref_result_nullonfailure_`

   Vrácený ukazatel odkazuje na platnou vyrovnávací paměť, pokud je funkce úspěšná, nebo null, pokud se funkce nezdaří. Tato anotace je pro referenční parametr.

## <a name="output-reference-parameters"></a>Výstupní referenční parametry

Běžné použití referenčního parametru je pro výstupní parametry. Pro jednoduché parametry výstupní `int&` `_Out_` referenční, jako je například , poskytuje správnou sémantiku. Však pokud výstupní hodnota je `int *&`ukazatel, jako je například `_Outptr_ int **` , ekvivalentní ukazatele poznámky jako neposkytují správnou sémantiku. Chcete-li výstižně vyjádřit sémantiku výstupních referenčních parametrů pro typy ukazatelů, použijte tyto složené poznámky:

### <a name="annotations-and-descriptions"></a>Poznámky a popisy

- `_Outref_`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null.

- `_Outref_result_maybenull_`

     Výsledek musí být platný v post-state, ale může být null v post-state.

- `_Outref_result_buffer_(s)`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null. Odkazuje na platnou `s` vyrovnávací paměť prvků velikosti.

- `_Outref_result_bytebuffer_(s)`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null. Odkazuje na platnou `s` vyrovnávací paměť bajtů velikosti.

- `_Outref_result_buffer_to_(s, c)`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null. Odkazuje na `s` vyrovnávací paměť prvků, `c` z nichž první jsou platné.

- `_Outref_result_bytebuffer_to_(s, c)`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null. Odkazuje na `s` vyrovnávací paměť bajtů, z nichž první `c` jsou platné.

- `_Outref_result_buffer_all_(s)`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null. Odkazuje na platnou `s` vyrovnávací paměť platných prvků velikosti.

- `_Outref_result_bytebuffer_all_(s)`

     Výsledek musí být platný v post-state a nemůže mít hodnotu null. Odkazuje na platnou vyrovnávací paměť `s` bajtů platných prvků.

- `_Outref_result_buffer_maybenull_(s)`

     Výsledek musí být platný v post-state, ale může být null v post-state. Odkazuje na platnou `s` vyrovnávací paměť prvků velikosti.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Výsledek musí být platný v post-state, ale může být null v post-state. Odkazuje na platnou `s` vyrovnávací paměť bajtů velikosti.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Výsledek musí být platný v post-state, ale může být null v post-state. Odkazuje na `s` vyrovnávací paměť prvků, `c` z nichž první jsou platné.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Výsledek musí být platný v post-state, ale může být null v post stavu. Odkazuje na `s` vyrovnávací paměť bajtů, z nichž první `c` jsou platné.

- `_Outref_result_buffer_all_maybenull_(s)`

     Výsledek musí být platný v post-state, ale může být null v post stavu. Odkazuje na platnou `s` vyrovnávací paměť platných prvků velikosti.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Výsledek musí být platný v post-state, ale může být null v post stavu. Odkazuje na platnou vyrovnávací paměť `s` bajtů platných prvků.

## <a name="return-values"></a>Vrácené hodnoty

Vrácená hodnota funkce se `_Out_` podobá parametru, ale je na jiné úrovni de-reference a není třeba vzít v úvahu koncept ukazatele na výsledek. Pro následující poznámky je vrácená hodnota objekt s anotovanými tóny – skalární, ukazatel na strukturu nebo ukazatel na vyrovnávací paměť. Tyto poznámky mají stejnou sémantiku `_Out_` jako odpovídající poznámky.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Formátovat parametry řetězce

- `_Printf_format_string_`Označuje, že parametr je formátovací `printf` řetězec pro použití ve výrazu.

     **Příklad**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`Označuje, že parametr je formátovací `scanf` řetězec pro použití ve výrazu.

     **Příklad**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`Označuje, že parametr je formátovací `scanf_s` řetězec pro použití ve výrazu.

     **Příklad**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Další běžné poznámky

### <a name="annotations-and-descriptions"></a>Poznámky a popisy

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Parametr, pole nebo výsledek je v rozsahu `low` (včetně) od do `hi`. Ekvivalentní, `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` který je použit na objekt s anotovanými notami spolu s příslušnými podmínkami před stavem nebo po stavu.

    > [!IMPORTANT]
    > Přestože názvy obsahují "in" a "out", `_In_` `_Out_` sémantiku a **nevztahují** se na tyto poznámky.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Hodnota s anotovanými `expr`notami je přesně . Ekvivalentní, `_Satisfies_(_Curr_ == expr)` který je použit na objekt s anotovanými notami spolu s příslušnými podmínkami před stavem nebo po stavu.

- `_Struct_size_bytes_(size)`

     Platí pro deklaraci struktury nebo třídy. Označuje, že platný objekt tohoto typu může být větší než deklarovaný `size`typ, přičemž počet bajtů je dán . Příklad:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Velikost vyrovnávací paměti v bajtů `pM` `MyStruct *` parametru typu je pak považován za:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Související prostředky

[Blog týmu pro analýzu kódu](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Viz také

- [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Porozumění SAL](../code-quality/understanding-sal.md)
- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
- [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)
- [Zadávání poznámek o chování při zamykání](../code-quality/annotating-locking-behavior.md)
- [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Vnitřní funkce](../code-quality/intrinsic-functions.md)
- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
