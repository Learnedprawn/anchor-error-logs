# anchor-error-logs

1.  Error: Signature verification failed.
    Missing signature for public key [`Hn74VuTHoWGDYCTW8HUAHoN3t8kvBPcZSwe7qMv1YY5v`].
    at Transaction.serialize (node_modules/@solana/web3.js/src/transaction/legacy.ts:828:15)
    at AnchorProvider.sendAndConfirm (node_modules/@coral-xyz/anchor/src/provider.ts:164:22)
    at processTicksAndRejections (node:internal/process/task_queues:105:5)
    at MethodsBuilder.rpc [as _rpcFn] (node_modules/@coral-xyz/anchor/src/program/namespace/rpc.ts:29:16)

Meaning: Missing signers account in the test

2.  Simulation failed.
    Message: Transaction simulation failed: Error processing Instruction 0: Cross-program invocation with unauthorized signer or writable account.
    Logs:
    [
    "Program BN61uwvvUDGr9RwdHt5MNxT3ci4VNVxiC9Uxh5zdVU7X invoke [1]",
    "Program log: Instruction: Release",
    "5GaqLG82jaNJ5FvogTa8d3PogmyzKfTHUMfcRtgvxk8r's writable privilege escalated",
    "Program BN61uwvvUDGr9RwdHt5MNxT3ci4VNVxiC9Uxh5zdVU7X consumed 10094 of 200000 compute units",
    "Program BN61uwvvUDGr9RwdHt5MNxT3ci4VNVxiC9Uxh5zdVU7X failed: Cross-program invocation with unauthorized signer or writable account"
    ].

Meaning:
a) Missing mut in a mutable account
b) Incorrect seeds passed in for a PDA signer account

3.        Simulation failed.
    Message: Transaction simulation failed: This transaction has already been processed.
    Logs:
    [].

Meaning: A similar signature instruction has been called in the same block and to avoid double spending it is being failed.
