找到两个排好序的数组的中位数


int find_k(vector<int>& nums1, vector<int>& nums2, int k) {
	if (nums1.size() + nums2.size() < k || k<=0)
		return 0;
	if (nums1.size() == 0)
		return nums2[k - 1];
	if (nums2.size() == 0)
		return nums1[k-1];
	int part1 = k / 2;
	int part2;
	int n1 = nums1.size();
	int n2 = nums2.size();
	part1 = part1 > n1 ? n1 : part1;
	part2 = k - part1;
	part2 = part2 > n2 ? n2 : part2;
	part1 = k - part2;
	if (nums1[part1 - 1] == nums2[part2 - 1])
		return nums1[part1 - 1];
	if (nums1[part1 - 1] > nums2[part2 - 1]) {
			while (part1 > 0 && part2 < nums2.size() && nums1[part1 - 1] > nums2[part2 - 1] && nums1[part1-1]>nums2[part2]){
				part1--;
				part2++;
			}
			if (part1 > 0 && part2 <= nums2.size())
				return max(nums1[part1 - 1], nums2[part2 - 1]);
			else
				return part1 > 0 ? nums1[part1 - 1] : nums2[part2 - 1];
			
		}
	else {
		while (part2 > 0 && part1 < nums1.size() && nums2[part2 - 1] > nums1[part1 - 1] && nums2[part2 - 1]>nums1[part1]) {
			part1++;
			part2--;
		}
		if (part2 > 0 && part1 <= nums1.size())
			return max(nums2[part2 - 1], nums1[part1 - 1]);
		else
			return part2 > 0 ? nums1[part2 - 1] : nums2[part1 - 1];
	}
}
