[Short Randomizable signatures](https://eprint.iacr.org/2015/525) by David Pointcheval and Olivier Sanders.  
Implementing signature scheme from section 6.1 of the paper as it allows for signing committed messages as well. Demonstrated by test `test_sig_committed_messages`.  
Implementing proof of knowledge of a signature from section 6.2 of paper. Demonstrated by test `test_PoK_sig`.  
In addition to proof of knowledge, the user can also reveal some of the messages under the signature without revealing all messages or signature.
Demonstrated in test `test_PoK_sig_reveal_messages`.  
A more comprehensive test where a user gets signature over a mix of messages where some of them are known while 
others are committed to and then a proof of knowledge is done for signature with selectively revealing some messages. Demonstrated in the test `test_scenario_1`.  

  
The groups for public key (*_tilde) and signatures can be flipped by compiling with feature `G1G2` or `G2G1`. These features are mutually exclusive. The default feature is `G2G1` meaning signatures are in group G1. 

To run tests with signature in group G1. The proof of knowledge of signatures will involve a multi-exponentiation in group G2.
```
cargo test --release --no-default-features --features G2G1
```

To run tests with signature in group G2. The proof of knowledge of signatures will involve a multi-exponentiation in group G1.
```
cargo test --release --no-default-features --features G1G2
```
