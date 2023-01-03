function apartmentHunting(blocks, reqs) {
    // Write your code here.
    //Make a map for each block with closest locations
    let hashMap = {};

    for(let req of reqs){
        hashMap[req] = blocks.map(()=>Infinity);
        for(let i in blocks){
            for(let dest in blocks){
                let dist = Math.abs(i-dest);
                if (blocks[dest][req] && dist<hashMap[req][i])
                    hashMap[req][i]=dist;
            }
        }
    }

    let result, resDist = Infinity;
    for (let i in blocks) {
        let maxDist = 0;
        for (let req of reqs)
            maxDist = Math.max(maxDist, hashMap[req][i]);
        if (resDist>maxDist) {
            result = i;
            resDist = maxDist;
        }
    }
    return result;
}

// Do not edit the line below.
exports.apartmentHunting = apartmentHunting;
