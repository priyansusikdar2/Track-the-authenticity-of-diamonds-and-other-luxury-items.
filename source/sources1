module MyModule::DiamondTracker {

    use aptos_framework::signer;

    /// Struct representing a diamond or luxury item.
    struct Item has store, key {
        id: u64,
        description: vector<u8>,
        registered: bool,
    }

    /// Function to register a new diamond or luxury item.
    public fun register_item(owner: &signer, id: u64, description: vector<u8>) {
        let item = Item {
            id,
            description,
            registered: true,
        };
        move_to(owner, item);
    }

    /// Function to verify the authenticity of a registered item.
    public fun verify_item(owner: &signer, id: u64): bool acquires Item {
        let item = borrow_global<Item>(signer::address_of(owner));
        assert!(item.id == id, 1);
        item.registered
    }
}
