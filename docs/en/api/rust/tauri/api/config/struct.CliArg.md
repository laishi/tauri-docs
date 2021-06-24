---
title: Struct tauri::api::config::CliArg
sidebar_label: struct.CliArg
---

# Struct tauri::api::config::CliArg,\[−],\[−],−

```rs
pub struct CliArg {
    pub short: Option<char>,
    pub name: String,
    pub description: Option<String>,
    pub long_description: Option<String>,
    pub takes_value: Option<bool>,
    pub multiple: Option<bool>,
    pub multiple_occurrences: Option<bool>,
    pub number_of_values: Option<u64>,
    pub possible_values: Option<Vec<String, Global>>,
    pub min_values: Option<u64>,
    pub max_values: Option<u64>,
    pub required: Option<bool>,
    pub required_unless_present: Option<String>,
    pub required_unless_present_all: Option<Vec<String, Global>>,
    pub required_unless_present_any: Option<Vec<String, Global>>,
    pub conflicts_with: Option<String>,
    pub conflicts_with_all: Option<Vec<String, Global>>,
    pub requires: Option<String>,
    pub requires_all: Option<Vec<String, Global>>,
    pub requires_if: Option<Vec<String, Global>>,
    pub required_if_eq: Option<Vec<String, Global>>,
    pub require_equals: Option<bool>,
    pub index: Option<u64>,
}
```

A CLI argument definition

## Fields

`short: Option<char>`

The short version of the argument, without the preceding -.

NOTE: Any leading - characters will be stripped, and only the first non - character will be used as the short version.

`name: String`

The unique argument name

`description: Option<String>`

The argument description which will be shown on the help information. Typically, this is a short (one line) description of the arg.

`long_description: Option<String>`

The argument long description which will be shown on the help information. Typically this a more detailed (multi-line) message that describes the argument.

`takes_value: Option<bool>`

Specifies that the argument takes a value at run time.

NOTE: values for arguments may be specified in any of the following methods

-   Using a space such as -o value or –option value
-   Using an equals and no space such as -o=value or –option=value
-   Use a short and no space such as -ovalue

`multiple: Option<bool>`

Specifies that the argument may appear more than once.

-   For flags, this results in the number of occurrences of the flag being recorded. For example -ddd or -d -d -d would count as three occurrences.
-   For options there is a distinct difference in multiple occurrences vs multiple values. For example, –opt val1 val2 is one occurrence, but two values. Whereas –opt val1 –opt val2 is two occurrences.

`multiple_occurrences: Option<bool>``number_of_values: Option<u64>``possible_values: Option<Vec<String, Global>>`

Specifies a list of possible values for this argument. At runtime, the CLI verifies that only one of the specified values was used, or fails with an error message.

`min_values: Option<u64>`

Specifies the minimum number of values for this argument. For example, if you had a -fargument where you wanted at least 2 ‘files’, you would set `minValues: 2`, and this argument would be satisfied if the user provided, 2 or more values.

`max_values: Option<u64>`

Specifies the maximum number of values are for this argument. For example, if you had a -fargument where you wanted up to 3 ‘files’, you would set .max_values(3), and this argument would be satisfied if the user provided, 1, 2, or 3 values.

`required: Option<bool>`

Sets whether or not the argument is required by default.

-   Required by default means it is required, when no other conflicting rules have been evaluated
-   Conflicting rules take precedence over being required.

`required_unless_present: Option<String>`

Sets an arg that override this arg’s required setting i.e. this arg will be required unless this other argument is present.

`required_unless_present_all: Option<Vec<String, Global>>`

Sets args that override this arg’s required setting i.e. this arg will be required unless all these other arguments are present.

`required_unless_present_any: Option<Vec<String, Global>>`

Sets args that override this arg’s required setting i.e. this arg will be required unless at least one of these other arguments are present.

`conflicts_with: Option<String>`

Sets a conflicting argument by name i.e. when using this argument, the following argument can’t be present and vice versa.

`conflicts_with_all: Option<Vec<String, Global>>`

The same as conflictsWith but allows specifying multiple two-way conflicts per argument.

`requires: Option<String>`

Tets an argument by name that is required when this one is present i.e. when using this argument, the following argument must be present.

`requires_all: Option<Vec<String, Global>>`

Sts multiple arguments by names that are required when this one is present i.e. when using this argument, the following arguments must be present.

`requires_if: Option<Vec<String, Global>>`

Allows a conditional requirement with the signature \[arg, value] the requirement will only become valid if `arg`’s value equals `${value}`.

`required_if_eq: Option<Vec<String, Global>>`

Allows specifying that an argument is required conditionally with the signature \[arg, value] the requirement will only become valid if the `arg`’s value equals `${value}`.

`require_equals: Option<bool>`

Requires that options use the –option=val syntax i.e. an equals between the option and associated value.

`index: Option<u64>`

The positional argument index, starting at 1.

The index refers to position according to other positional argument. It does not define position in the argument list as a whole. When utilized with multiple=true, only the last positional argument may be defined as multiple (i.e. the one with the highest index).

## Trait Implementations

### `impl Clone for CliArg`

#### `pub fn clone(&self) -> CliArg`

Returns a copy of the value. [Read more](https://doc.rust-lang.org/nightly/core/clone/trait.Clone.html#tymethod.clone)

#### `pub fn clone_from(&mut self, source: &Self)`1.0.0[\[src\]](https://doc.rust-lang.org/nightly/src/core/clone.rs.html#130 "goto source code")

Performs copy-assignment from `source`. [Read more](https://doc.rust-lang.org/nightly/core/clone/trait.Clone.html#method.clone_from)

### `impl Debug for CliArg`

#### `pub fn fmt(&self, f: &mut Formatter<'_>) -> Result<(), Error>`

Formats the value using the given formatter. [Read more](https://doc.rust-lang.org/nightly/core/fmt/trait.Debug.html#tymethod.fmt)

### `impl Default for CliArg`

#### `pub fn default() -> CliArg`

Returns the “default value” for a type. [Read more](https://doc.rust-lang.org/nightly/core/default/trait.Default.html#tymethod.default)

### `impl<'de> Deserialize<'de> for CliArg`

#### `pub fn deserialize<__D>( __deserializer: __D ) -> Result<CliArg, <__D as Deserializer<'de>>::Error> where __D: Deserializer<'de>,`

Deserialize this value from the given Serde deserializer. [Read more](https://docs.rs/serde/1.0.126/serde/de/trait.Deserialize.html#tymethod.deserialize)

### `impl PartialEq<CliArg> for CliArg`

#### `pub fn eq(&self, other: &CliArg) -> bool`

This method tests for `self` and `other` values to be equal, and is used by `==`. [Read more](https://doc.rust-lang.org/nightly/core/cmp/trait.PartialEq.html#tymethod.eq)

#### `pub fn ne(&self, other: &CliArg) -> bool`

This method tests for `!=`.

### `impl StructuralPartialEq for CliArg`

### `impl ToTokens for CliArg`

#### `pub fn to_tokens(&self, tokens: &mut TokenStream)`

Write `self` to the given `TokenStream`. [Read more](https://docs.rs/quote/1.0.9/quote/to_tokens/trait.ToTokens.html#tymethod.to_tokens)

#### `pub fn to_token_stream(&self) -> TokenStream`[\[src\]](https://docs.rs/quote/1.0.9/src/quote/to_tokens.rs.html#61 "goto source code")

Convert `self` directly into a `TokenStream` object. [Read more](https://docs.rs/quote/1.0.9/quote/to_tokens/trait.ToTokens.html#method.to_token_stream)

#### `pub fn into_token_stream(self) -> TokenStream`[\[src\]](https://docs.rs/quote/1.0.9/src/quote/to_tokens.rs.html#71-73 "goto source code")

Convert `self` directly into a `TokenStream` object. [Read more](https://docs.rs/quote/1.0.9/quote/to_tokens/trait.ToTokens.html#method.into_token_stream)

## Auto Trait Implementations

### `impl RefUnwindSafe for CliArg`

### `impl Send for CliArg`

### `impl Sync for CliArg`

### `impl Unpin for CliArg`

### `impl UnwindSafe for CliArg`

## Blanket Implementations

### `impl<T> Any for T where T: 'static + ?Sized,`[\[src\]](https://doc.rust-lang.org/nightly/src/core/any.rs.html#131-135 "goto source code")

#### `pub fn type_id(&self) -> TypeId`[\[src\]](https://doc.rust-lang.org/nightly/src/core/any.rs.html#132 "goto source code")

Gets the `TypeId` of `self`. [Read more](https://doc.rust-lang.org/nightly/core/any/trait.Any.html#tymethod.type_id)

### `impl<T> Borrow<T> for T where T: ?Sized,`[\[src\]](https://doc.rust-lang.org/nightly/src/core/borrow.rs.html#208-213 "goto source code")

#### `pub fn borrow(&self) -> &T`[\[src\]](https://doc.rust-lang.org/nightly/src/core/borrow.rs.html#210 "goto source code")

Immutably borrows from an owned value. [Read more](https://doc.rust-lang.org/nightly/core/borrow/trait.Borrow.html#tymethod.borrow)

### `impl<T> BorrowMut<T> for T where T: ?Sized,`[\[src\]](https://doc.rust-lang.org/nightly/src/core/borrow.rs.html#216-220 "goto source code")

#### `pub fn borrow_mut(&mut self) -> &mutT`[\[src\]](https://doc.rust-lang.org/nightly/src/core/borrow.rs.html#217 "goto source code")

Mutably borrows from an owned value. [Read more](https://doc.rust-lang.org/nightly/core/borrow/trait.BorrowMut.html#tymethod.borrow_mut)

### `impl<'de, D, P> CommandArg<'de, P> for D where P: Params, D: Deserialize<'de>,`[\[src\]](/docs/api/rust/tauri/../../../src/tauri/command.rs#47-52 "goto source code")

#### `pub fn from_command(CommandItem<'de, P>) -> Result<D, InvokeError>`[\[src\]](/docs/api/rust/tauri/../../../src/tauri/command.rs#48-51 "goto source code")

Derives an instance of `Self` from the [`CommandItem`](/docs/api/rust/tauri/../../../tauri/command/struct.CommandItem "CommandItem"). [Read more](/docs/api/rust/tauri/../../../tauri/command/trait.CommandArg#tymethod.from_command)

### `impl<T> DeserializeOwned for T where T: for<'de> Deserialize<'de>,`[\[src\]](https://docs.rs/serde/1.0.126/src/serde/de/mod.rs.html#603 "goto source code")

### `impl<T> From<T> for T`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#544-548 "goto source code")

#### `pub fn from(t: T) -> T`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#545 "goto source code")

Performs the conversion.

### `impl<T, U> Into<U> for T where U: From<T>,`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#533-540 "goto source code")

#### `pub fn into(self) -> U`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#537 "goto source code")

Performs the conversion.

### `impl<T> ToOwned for T where T: Clone,`[\[src\]](https://doc.rust-lang.org/nightly/src/alloc/borrow.rs.html#81-93 "goto source code")

#### `type Owned = T`

The resulting type after obtaining ownership.

#### `pub fn to_owned(&self) -> T`[\[src\]](https://doc.rust-lang.org/nightly/src/alloc/borrow.rs.html#86 "goto source code")

Creates owned data from borrowed data, usually by cloning. [Read more](https://doc.rust-lang.org/nightly/alloc/borrow/trait.ToOwned.html#tymethod.to_owned)

#### `pub fn clone_into(&self, target: &mutT)`[\[src\]](https://doc.rust-lang.org/nightly/src/alloc/borrow.rs.html#90 "goto source code")

🔬 This is a nightly-only experimental API. (`toowned_clone_into`)

recently added

Uses borrowed data to replace owned data, usually by cloning. [Read more](https://doc.rust-lang.org/nightly/alloc/borrow/trait.ToOwned.html#method.clone_into)

### `impl<T, U> TryFrom<U> for T where U: Into<T>,`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#581-590 "goto source code")

#### `type Error = Infallible`

The type returned in the event of a conversion error.

#### `pub fn try_from(value: U) -> Result<T, <T as TryFrom<U>>::Error>`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#587 "goto source code")

Performs the conversion.

### `impl<T, U> TryInto<U> for T where U: TryFrom<T>,`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#567-576 "goto source code")

#### `type Error = <U as TryFrom<T>>::Error`

The type returned in the event of a conversion error.

#### `pub fn try_into(self) -> Result<U, <U as TryFrom<T>>::Error>`[\[src\]](https://doc.rust-lang.org/nightly/src/core/convert/mod.rs.html#573 "goto source code")

Performs the conversion.

### `impl<V, T> VZip<V> for T where V: MultiLane<T>,`

#### `pub fn vzip(self) -> V`