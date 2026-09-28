## Versions
anchor-cli 1.1.2 · node 24.10.0 · @codama/cli 1.6.3

## TODO 3
Required: fundraiser, vault. Optional: contributorAccount, contributorAta,
tokenProgram, systemProgram. In `contribute`, the fundraiser PDA is seeded on
`fundraiser.maker` and the vault ATA on `fundraiser.mint_to_raise`, both fields
stored inside the fundraiser account, and the builder only has the inputs it is
given, never account data, so it would need the fundraiser to find the
fundraiser. `contributorAccount` and `contributorAta` are seeded only on
accounts the caller already passes (`fundraiser`, `contributor`,
`mint_to_raise`), and `initialize` seeds the fundraiser on the `maker` account
instead, which is why it is optional there.

## Bonus
not attempted

## One thing that surprised me
Plain `anchor test` ran zero tests. The script's unquoted `tests/**/*.ts` is
expanded by the shell with `**` acting as a single `*`, so it matches only
`tests/helpers/kit-adapter.ts` and Mocha never sees the real test files.
`anchor test tests/*.ts` runs them all.
