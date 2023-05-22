pcl::PointXYZ::PointXYZ getRandomPointFrom3DRing(std::vector<float>& center,  float R,  float r){
	float norm_of_point = 0;
	std::random_device rd;
	std::mt19937 gen(rd());
	std::uniform_real_distribution<float> dis(0,R - r);
	std::uniform_real_distribution<float> dis2(-1,1);
	pcl::PointXYZ::PointXYZ rand_vec = PointXYZ(dis2(gen), dis2(gen), dis2(gen));
	float norm_of_rand_vec = 0;
	float v = dis(gen) + r;
	for(int i=0; i<rand_vec.size(); i++){
		norm_of_rand_vec += (rand_vec[i] * rand_vec[i]); }
		
	norm_of_rand_vec = std::sqrt(norm_of_rand_vec);
	for(int i=0; i<rand_vec.size(); i++){
		rand_vec[i] = rand_vec[i] / norm_of_rand_vec * v + center[i]; 
		}
		return rand_vec;
		
}
